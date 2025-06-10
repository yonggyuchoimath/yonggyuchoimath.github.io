---
layout: page
permalink: /seminars/
title: seminars
description: # seminars
nav: true
nav_order: 5
---

<!-- For now, this page is assumed to be a static description of your courses. You can convert it to a collection similar to `_seminars/` so that you can have a dedicated page for each course.

Organize your courses by years, topics, or universities, however you like! -->


<!-- pages/seminars.md -->
<div class="seminars">
{% if site.enable_seminar_categories and page.display_categories %}
  <!-- Display categorized seminars -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_seminars = site.seminars | where: "category", category %}
  {% assign sorted_seminars = categorized_seminars | sort: "importance" %}
  <!-- Generate cards for each seminar -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for seminar in sorted_seminars %}
      {% include seminars_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for seminar in sorted_seminars %}
      {% include seminars.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display seminars without categories -->

{% assign sorted_seminars = site.seminars | sort: "importance" %}

  <!-- Generate cards for each seminar -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for seminar in sorted_seminars %}
      {% include seminars_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for seminar in sorted_seminars %}
      {% include seminars.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
