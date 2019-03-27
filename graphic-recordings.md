---
layout: default
title: "Graphic Recordings"
permalink: /graphic-recordings/
---

<h1>{{ page.title }}</h1>

{% assign count = 0 %}
{% assign align = "left" %}
{% for gallery in site.data.galleries.posters %}
{% if count == 0 %}<div class="row">{% endif %}
  <div class="half-width gallery-preview {{ align }}">
    <h1>{{ gallery.title }}</h1>
    <a href="{{ site.url }}{{ site.baseurl }}/graphic-recordings/{{ gallery.directory | remove:'poster_' }}.html">
      <img alt="{{ gallery.title }}" src="{{ site.url }}{{ site.baseurl }}/images/{% if gallery.picture_path %}{{ gallery.picture_path }}{% else %}{{ gallery.directory }}{% endif %}/{{ gallery.preview.thumbnail }}" />
    </a>
  </div>
{% if count == 1 %}</div>{% endif %}
{% assign count = count | plus: 1 %}
{% assign align = "right" %}
{% if count >= 2 %}
{% assign align = "left" %}
{% assign count = 0 %}
{% endif %}
{% endfor %}
