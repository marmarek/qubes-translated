---
lang: fr
layout: doc
permalink: /fr/doc/templates/fedora-xfce/
ref: 61
title: The Fedora Xfce TemplateVM
translated: 'yes'
---

The Fedora Xfce TemplateVM
=====================

If you would like to use Fedora Xfce (more lightweight compared to GNOME desktop environment) Linux distribution in your qubes, you can install one of the available Fedora Xfce templates.


Installing
----------

To install a specific Fedora Xfce TemplateVM that is not currently installed in your system, use the following command in dom0:

    $ sudo qubes-dom0-update --enablerepo=qubes-templates-itl qubes-template-fedora-XX-xfce

   (Replace `XX` with the Fedora Xfce version number of the template you wish to install.)

To reinstall a Fedora Xfce TemplateVM that is already installed in your system, see [How to Reinstall a TemplateVM].


Upgrading
---------

To upgrade your Fedora TemplateVM, please see [Upgrading Fedora TemplateVMs].

[Upgrading Fedora TemplateVMs]: /fr/doc/template/fedora/upgrade/
[How to Reinstall a TemplateVM]: /fr/doc/reinstall-template/