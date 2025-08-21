---
layout: about
title:
permalink: /
subtitle: Hello! I'm Michael! I'm a new Masters Graduate in Robotics from the University of Pennsylvania.

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  more_info: >
    MS Robotics, University of Pensylvannia 2025. BS Computer Engineering, UCSD 2023.

selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: false # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

display_categories: [work]
horizontal: true


latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

##### My main interest is in resource-constrained robotics - to design, build, and control robots that don't have to rely exclusively on expensive, high-end hardware by exploiting the underlying controls and embedded systems. My experience is grounded in embedded systems, control, and backend systems with additional experience in networking, architecture, and software engineering.

I'm currently working on updating the hardware and firmware infrastructure for the IoT edge devices course (ESE 5160) at the University of Pennsylvania.
<br>
<br>
<br>
<br>
<br>
<br><br>
<br>
<br>


<div class="projects">
<h2><a href="{{ '/projects/' | relative_url }}">Projects</a></h2>
<hr>
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md">
    {% for project in sorted_projects limit:3 %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects limit:3%}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects limit:3 %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects limit:3 %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
