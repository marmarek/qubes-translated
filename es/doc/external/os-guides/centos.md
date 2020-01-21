---
lang: es
layout: doc
permalink: /doc/templates/centos/
ref: 183
title: CentOS Template
---

# CentOS Template

If you would like to use a stable, predictable, manageable and reproducible distribution in your AppVMs, you can install the CentOS template, provided by Qubes in ready to use binary package.

For the minimal version, please see [Minimal TemplateVMs](/doc/templates/minimal/)


## Instalación

CentOS-7 can be installed with the following command:

    [user@dom0 ~]$ sudo qubes-dom0-update --enablerepo=qubes-templates-community qubes-template-centos-7

To switch, reinstall and uninstall a CentOS TemplateVM that is already installed in your system, see *How to [switch], [reinstall] and [uninstall]*.

#### After Installing

After a fresh install, we recommend to [Update the TemplateVM](/doc/software-update-vm/).

## Want to contribute?

*   [¿Cómo puedo contribuir al Qubes Project?](/doc/contributing/)

*   [Directrices para contribuidores a la documentación](/doc/doc-guidelines/)

[switch]: /doc/templates/#switching
[reinstall]: /doc/reinstall-template/
[uninstall]: /doc/templates/#uninstalling
