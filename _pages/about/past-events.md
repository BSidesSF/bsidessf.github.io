---
layout: page
title: "Past Events"
---

{% for hist in site.data.history %}
* {{ hist.year }}:
  {% for cat in hist.categories %}
    {% if cat.href %}
  * <a href="{{ cat.href }}">{{ cat.title }}</a>
    {% endif %}
    {% if cat.external %}
  * <a href="{{ cat.external }}" target="_blank">{{ cat.title }} (external)</a>
    {% endif %}
  {% endfor %}
{% endfor %}
