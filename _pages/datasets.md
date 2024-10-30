---
layout: page
title: datasets
permalink: /datasets/
description: A growing collection of your cool datasets.
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

<!-- pages/datasets.md -->
<div class="datasets">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized datasets -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_datasets = site.datasets | where: "category", category %}
  {% assign sorted_datasets = categorized_datasets | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_datasets %}
      {% include datasets_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_datasets %}
      {% include datasets.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display datasets without categories -->

{% assign sorted_datasets = site.datasets | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_datasets %}
      {% include datasets_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_datasets %}
      {% include datasets.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
