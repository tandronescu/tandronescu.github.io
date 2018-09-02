---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

<head>
<link rel="stylesheet" type="text/css" href="/assets/css/projects.css">
</head>

Here are some of my personal favourite projects I have worked on organized by their respective engineering discipline. Projects are listed multiple times since they combine multiple disciplines. They are further categorized using tags below the table. More software projects are available on my github profile. 

<table>
    <tr>
        <td> Software </td>
        <td> Electrical </td>
        <td> Mechanical </td>
    </tr>
    <tr>
        <td>
            <ul>
                <li> <a href="/Virtual-Cane/" class="project-link-duplicate"> Virtual White Cane </a> </li>
                <li> <a href="/Username-Generator/" class="project-link"> Username Generator </a> </li>
                <li> <a href="/Survival-Game/" class="project-link"> Survival Game </a> </li>
                <li> <a href="/Arduino-Projects/" class="project-link-duplicate"> Arduino Projects </a> </li>
            </ul>
        </td>
        <td>
            <ul>
                <li> <a href="/Electric-Longboard/" class="project-link-duplicate">Electric Longboard </a> </li>
                <li> <a href="/Arduino-Projects/" class="project-link-duplicate"> Arduino Projects </a> </li>
                <li> <a href="/Robot-Arm/" class="project-link-duplicate"> Mechanical Robot Arm </a> </li>
            </ul>
        </td>
        <td>
            <ul>
                <li> <a href="/Electric-Longboard/" class="project-link-duplicate">Electric Longboard </a> </li>
                <li> <a href="/Virtual-Cane/" class="project-link-duplicate"> Virtual White Cane </a> </li>
                <li> <a href="/Robot-Arm/" class="project-link-duplicate"> Mechanical Robot Arm </a> </li>
            </ul>
        </td>
    </tr>
</table>

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}