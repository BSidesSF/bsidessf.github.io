---
layout: page
title: "Sponsors"
---

Our fantastic sponsors make BSidesSF financially possible year after year, none of this is possible without them!

<h3><a href="/sponsors/benefits/">Interested in sponsoring?</a></h3>

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

<center>
  <p>
    Have further questions about sponsorships? Contact <a href="mailto:sponsors@bsidessf.org">sponsors@bsidessf.org</a>.
  </p>
  <p>
    <em>All names and logos are property of their respective owners.</em>
  </p>
  <p>
    <em>
      {% for class in site.data.sponsors.levels %}
        {% for sponsor in class.sponsors %}
          {{ sponsor.credits }}
        {% endfor %}
      {% endfor %}
    </em>
  </p>
</center>
