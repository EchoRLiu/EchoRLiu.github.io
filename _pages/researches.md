---
layout: page
title: research
permalink: /research/
description: Here are some projects I am working on or have worked on before.
nav: true
nav_order: 2
display_categories: [current, past]
horizontal: false
---

<!-- pages/researches.md -->
<div class="researches">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized researches -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_researches = site.researches | where: "category", category -%}
  {%- assign sorted_researches = categorized_researches | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_researches -%}
      {% include projects_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_researches -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display researches without categories -->
  {%- assign sorted_researches = site.researches | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_researches -%}
      {% include projects_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_researches -%}
      {% include projects.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>