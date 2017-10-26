---
layout: page
active: assignments
title: "Assignments"
---

# {{ page.title }}

## Labs

{% for pair in site.data.assignments %}
  {% assign name = pair[0] %}
  {% assign assignment = pair[1] %}

  {% if assignment.type == 'lab' %}
- [{{ assignment.title }} - {{ assignment.subtitle }}]({{ name }}) due {{ assignment.due }}
  {% endif %}
{% endfor %}


## Programs

{% for pair in site.data.assignments %}
  {% assign name = pair[0] %}
  {% assign assignment = pair[1] %}

  {% if assignment.type == 'program' %}
- [{{ assignment.title }} - {{ assignment.subtitle }}]({{ name }}) due {{ assignment.due }}
  {% endif %}
{% endfor %}

