---
layout: page
active: assignments
title: "Assignments"
---

# {{ page.title }}

## Final Project

[Final Project Description](final)


## Programs

Either individual or pair-programming (see each assignment page):

{% for pair in site.data.assignments %}
  {% assign name = pair[0] %}
  {% assign assignment = pair[1] %}

  {% if assignment.type == 'lab' %}
- [{{ assignment.title }} - {{ assignment.subtitle }}]({{ name }}) due {{ assignment.due }}
  {% endif %}
{% endfor %}
