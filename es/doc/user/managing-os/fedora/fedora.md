---
lang: es
layout: doc
permalink: /es/doc/templates/fedora/
ref: 59
title: The Fedora TemplateVM
translated: 'yes'
---

# The Fedora TemplateVM

The Fedora [TemplateVM] is the default TemplateVM in Qubes OS. This page is about the standard (or "full") Fedora TemplateVM. For the minimal and Xfce versions, please see the [Minimal TemplateVMs] and [Fedora Xfce] pages.


## Instalando

To [install] a specific Fedora TemplateVM that is not currently installed in your system, use the following command in dom0:

    $ sudo qubes-dom0-update qubes-template-fedora-XX

   (Replace `XX` with the Fedora version number of the template you wish to install.)

To reinstall a Fedora TemplateVM that is already installed in your system, see [How to Reinstall a TemplateVM].


## After Installing

After installing a fresh Fedora TemplateVM, we recommend performing the following steps:

1. [Update the TemplateVM].

2. [Switch any TemplateBasedVMs that are based on the old TemplateVM to the new one][switch].

3. If desired, [uninstall the old TemplateVM].


## Actualizar

Please see [Updating software in TemplateVMs].


## Upgrading

Please see [Upgrading Fedora TemplateVMs].


## Release-specific notes

This section contains notes about specific Fedora releases.

(There is currently no release-specific information documented.)


[TemplateVM]: /es/doc/templates/
[Fedora Xfce]: /es/doc/templates/fedora-xfce/
[Minimal TemplateVMs]: /es/doc/templates/minimal/
[end-of-life]: https://fedoraproject.org/wiki/Fedora_Release_Life_Cycle#Maintenance_Schedule
[supported]: /es/doc/supported-versions/#templatevms
[How to Reinstall a TemplateVM]: /es/doc/reinstall-template/
[Update the TemplateVM]: /es/doc/software-update-vm/
[switch]: /es/doc/templates/#switching
[uninstall the old TemplateVM]: /es/doc/templates/#uninstalling
[Updating software in TemplateVMs]: /es/doc/software-update-domu/#updating-software-in-templatevms
[Upgrading Fedora TemplateVMs]: /es/doc/template/fedora/upgrade/
[install]: /es/doc/templates/#installing