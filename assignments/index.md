---
layout: page
active: assignments
title: "Assignments"
---

# {{ page.title }}

## Final Project

[Final Project Description](final)

### Components/Deliverables:

{% for pair in site.data.assignments %}
  {% assign name = pair[0] %}
  {% assign assignment = pair[1] %}

  {% if assignment.type == 'project' %}
- [{{ assignment.title }}]({{ name }}) due {{ assignment.due }}
  {% endif %}
{% endfor %}


## Programs

### Pair-programming lab:

{% for pair in site.data.assignments %}
  {% assign name = pair[0] %}
  {% assign assignment = pair[1] %}

  {% if assignment.type == 'lab' %}
- [{{ assignment.title }} - {{ assignment.subtitle }}]({{ name }}) due {{ assignment.due }}
  {% endif %}
{% endfor %}

### In-class workshops:

{% for pair in site.data.assignments %}
  {% assign name = pair[0] %}
  {% assign assignment = pair[1] %}

  {% if assignment.type == 'workshop' %}
- [{{ assignment.title }} - {{ assignment.subtitle }}]({{ name }}) on {{ assignment.date }}
  {% endif %}
{% endfor %}

