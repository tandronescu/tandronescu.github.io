---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

<head>
<link rel="stylesheet" type="text/css" href="/assets/css/projects.css">
</head>

Here are some of my favourite projects I have worked on. 

<ul>
    <li> <a href="/Electric-Longboard/" class="project-link-duplicate">Electric Longboard </a> </li>
    <li> <a href="/Communication-Base-Station/" class="project-link-duplicate"> Communication Base Station </a> </li>
</ul>

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}