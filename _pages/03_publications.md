---
layout: page
permalink: /publications/
title: publications
description: Peer-reviewed journals and conferences by categories in reversed chronological order.

journal_years: [2021, 2020, 2019, 2017, 2015]
conference_years: [2020, 2019, 2018, 2017, 2016, 2014, 2012]
---

## **Journals**
{% for y in page.journal_years %}
  <h3 class="year">{{y}}</h3>
  {% bibliography -f journals -q @*[year={{y}}]* %}
{% endfor %}

*: Equal contribution

## **Conferences**
{% for y in page.conference_years %}
  <h3 class="year">{{y}}</h3>
  {% bibliography -f conferences -q @*[year={{y}}]* %}
{% endfor %}
