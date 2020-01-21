---
lang: fr
layout: doc
permalink: /fr/doc/templates/centos/
ref: 183
title: CentOS Template
translated: 'yes'
---

# CentOS Template

If you would like to use a stable, predictable, manageable and reproducible distribution in your AppVMs, you can install the CentOS template, provided by Qubes in ready to use binary package.

For the minimal version, please see [Minimal TemplateVMs](/fr/doc/templates/minimal/)


## Installation

CentOS-7 can be installed with the following command:

    [user@dom0 ~]$ sudo qubes-dom0-update --enablerepo=qubes-templates-community qubes-template-centos-7

To switch, reinstall and uninstall a CentOS TemplateVM that is already installed in your system, see *How to [switch], [reinstall] and [uninstall]*.

#### After Installing

After a fresh install, we recommend to [Update the TemplateVM](/fr/doc/software-update-vm/).

## Want to contribute?

*   [How can I contribute to the Qubes Project?](/fr/doc/contributing/)

*   [Guidelines for Documentation Contributors](/fr/doc/doc-guidelines/)

[switch]: /fr/doc/templates/#switching
[reinstall]: /fr/doc/reinstall-template/
[uninstall]: /fr/doc/templates/#uninstalling