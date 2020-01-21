---
lang: es
layout: doc
permalink: /es/security/canaries/
redirect_from:
- /es/doc/canaries/
ref: 164
title: Canaries
translated: 'yes'
---

Qubes Canaries
==============

Qubes Canaries are published through the [Qubes Security Pack](/es/security/pack/).

<table>
  <tr>
    <th title="Anchor Link"><span class="fa fa-link"></span></th>
    <th>Date</th>
    <th>Qubes Canary</th>
  </tr>
{% for canary in site.data.canary reversed %}
  <tr id="{{ canary.canary }}">
    <td><a href="#{{ canary.canary }}" class="fa fa-link black-icon" title="Anchor link to Qubes Canary row: Qubes Canary #{{ canary.canary }}"></a></td>
    <td>{{ canary.date }}</td>
    <td><a href="https://github.com/QubesOS/qubes-secpack/blob/master/canaries/canary-{{ canary.canary }}-{{ canary.date | date: '%Y' }}.txt">Qubes Canary #{{ canary.canary }}</a></td>
  </tr>
{% endfor %}
</table>