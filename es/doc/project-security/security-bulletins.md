---
lang: es
layout: doc
permalink: /es/security/bulletins/
redirect_from:
- /es/doc/security-bulletins/
- /es/doc/security-bulletins/
- /es/doc/SecurityBulletins/
- /es/wiki/SecurityBulletins/
- /es/trac/wiki/SecurityBulletins/
ref: 156
title: Qubes Security Bulletins
translated: 'yes'
---

Qubes Security Bulletins (QSBs)
===============================

Qubes Security Bulletins (QSBs) are published through the [Qubes Security Pack](/es/security/pack/).

<table>
  <tr>
    <th title="Anchor Link"><span class="fa fa-link"></span></th>
    <th>Date</th>
    <th>Qubes Security Bulletin</th>
  </tr>
{% for qsb in site.data.qsb reversed %}
  <tr id="{{ qsb.qsb }}">
    <td><a href="#{{ qsb.qsb }}" class="fa fa-link black-icon" title="Anchor link to QSB row: QSB #{{ qsb.qsb }}"></a></td>
    <td>{{ qsb.date }}</td>
    <td><a href="https://github.com/QubesOS/qubes-secpack/blob/master/QSBs/qsb-{{ qsb.qsb }}-{{ qsb.date | date: '%Y' }}.txt">QSB #{{ qsb.qsb }}: {{ qsb.title | truncate: 68 }}</a></td>
  </tr>
{% endfor %}
</table>