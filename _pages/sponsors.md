---
layout: page
title: "Sponsors"
---

Our fantastic sponsors make BSidesSF financially possible year after year, 
none of this is possible without them!

We're currently planning 2026, if you would like to be a sponsor please 
see our [sponsorship kit](/sponsors/kit) for more
information.

You can also [email us](mailto:sponsors@bsidessf.org) when you want to discuss your
sponsorhip goals and options.

Thank you to all of the amazing sponsors below that made 2025 into a an amazing
event.


{% for class in site.data.sponsors.levels %}

  <div style="text-align: center;" class="sponsors {{ class.class }}">
    {% if class.level %}
      <h1>{{ class.level }}</h1>
    {% endif %}
    <div class="row">
      {% for sponsor in class.sponsors %}
        {% if sponsor.break %}
          </div><div class="row">
          {% continue %}
        {% endif %}
        <div class="column">
          {% if sponsor.type %}
            <h1 class="sponsors">{{ sponsor.type }}</h1>
          {% endif %}
          {% if sponsor.name == "Could Be You!" %}
            <a href="{{ site.data.sponsors.sponsorship_kit_url }}" target="_blank">
          {% else %}
            <a href="{{ sponsor.href }}" target="_blank">
          {% endif %}
            <div class="imgdiv">
              {% if sponsor.logo %}
                <img src="{{ site.url }}{{baseurl}}{{ sponsor.logo }}" alt="{{ sponsor.name }}" title="{% if sponsor.text %}{{ sponsor.text }}{% else %}{{ sponsor.name }}{% endif %}" />
              {% else %}
                <p><strong>{{ sponsor.name }}</strong></p>
              {% endif %}
            </div>
          </a>
        </div>
      {% endfor %}
    </div>
  </div>
{% endfor %}
