---
lang: es
layout: doc
permalink: /doc/dom0-secure-updates/
redirect_from:
- /en/doc/dom0-secure-updates/
- /doc/Dom0SecureUpdates/
- /wiki/Dom0SecureUpdates/
ref: 141
title: Dom0 Secure Updates
---

Qubes Dom0 secure update procedure
==================================

Reasons for Dom0 updates
------------------------

Normally there should be few reasons for updating software in Dom0. This is because there is no networking in Dom0, which means that even if some bugs will be discovered e.g. in the Dom0 Desktop Manager, this really is not a problem for Qubes, because all the third-party software running in Dom0 is not accessible from VMs or network in any way. Some exceptions to the above include: Qubes GUI daemon, Xen store daemon, and disk back-ends (we plan to move the disk backends to untrusted domain in Qubes 2.0). Of course we believe this software is reasonably secure and we hope it will not need patching.

Sin embargo, anticipamos se podrían requerir algunas otras situaciones al actualizar el software del Dom0:

-   Updating drivers/libs for new hardware support
-   Correcting non-security related bugs (e.g. new buttons for qubes manager)
-   Adding new features (e.g. GUI backup tool)

Problems with traditional network-based update mechanisms
---------------------------------------------------------

Dom0 is the most trusted domain on Qubes OS, and for this reason we decided to design Qubes in such a way that Dom0 is not connected to any network. In fact only certain domains can be connected to a network via so-called network domains. There can also be more than one network domain, e.g. in case the user is connected to more than one physically or logically separated networks.

Secure update mechanism we use in Qubes (starting from Beta 2)
-------------------------------------------------------------

No obstante, mantener el Dom0 no conectado a red alguna dificulta proporcionar actualizaciones para el software en el Dom0. Por esta razón hemos preparado el siguiente mecanismo para actualizaciones en el Dom0, que minimiza la cantidad de datos entrantes sin confianza procesados por el software del Dom0:

The update process is initiated by [qubes-dom0-update script](https://github.com/QubesOS/qubes-core-admin-linux/blob/release2/dom0-updates/qubes-dom0-update), running in Dom0.

Updates (\*.rpm files) are checked and downloaded by UpdateVM, which by default is the same as the firewall VM, but can be configured to be any other, network-connected VM. This is done by [qubes-download-dom0-updates.sh script](https://github.com/QubesOS/qubes-core-agent-linux/blob/release2/misc/qubes-download-dom0-updates.sh) (this script is executed using qrexec by the previously mentioned qubes-dom0-update). Note that we assume that this script might get compromised and fetch maliciously compromised downloads -- this is not a problem as Dom0 verifies digital signatures on updates later. The downloaded rpm files are placed in a ~~~/var/lib/qubes/dom0-updates~~~ directory on UpdateVM filesystem (again, they might get compromised while being kept there, still this isn't a problem). This directory is passed to yum using the ~~~--installroot=~~~ option.

Once updates are downloaded, the update script that runs in UpdateVM requests an RPM service [qubes.ReceiveUpdates](https://github.com/QubesOS/qubes-core-admin-linux/blob/release2/dom0-updates/qubes.ReceiveUpdates) to be executed in Dom0. This service is implemented by [qubes-receive-updates script](https://github.com/QubesOS/qubes-core-admin-linux/blob/release2/dom0-updates/qubes-receive-updates) running in Dom0. The Dom0's qubes-dom0-update script (which originally initiated the whole update process) waits until qubes-receive-updates finished.

The qubes-receive-updates script processes the untrusted input from Update VM: it first extracts the received \*.rpm files (that are sent over qrexec data connection) and then verifies digital signature on each file. The qubes-receive-updates script is a security-critical component of the Dom0 update process (as is the [qfile-dom0-unpacker.c](https://github.com/QubesOS/qubes-core-admin-linux/blob/release2/dom0-updates/qfile-dom0-unpacker.c) and the rpm utility, both used by the qubes-receive-updates for processing the untrusted input).

Una vez que qubes-receive-updates termine de desempaquetar y verificar las actualizaciones, estas se sitúan en el directorio ``qubes-receive-updates`` en el sistema de ficheros del Dom0. Esas actualizaciones ahora son de confianza. El Dom0 se configura (vea /etc/yum.conf en el Dom0) para que use este directorio como [repositorio yum](https://github.com/QubesOS/qubes-core-admin-linux/blob/release2/dom0-updates/qubes-cached.repo) predeterminado (y único).

Finally, qubes-dom0-update runs ``yum update`` that fetches the rpms from qubes-cached repo and installs them as usual.

Security benefit of our update mechanism
----------------------------------------

La ventaja del esquema de anterior es que uno no necesita confiar en la pila TCP/IP, la pila HTTP, y la implementación de wget, para entregar e instalar actualizaciones en el Dom0. Uno sólo necesita confiar en unos pocos cientos de líneas de código, tal como se discutió con anterioridad, así como en la utilidad rpm, para comprobar adecuadamente la firma digital (aunque esto es requisito en cualquier esquema de actualización).
