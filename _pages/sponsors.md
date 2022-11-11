---
layout: page
title: "Sponsors"
---

<h3>Interested in sponsoring? Check out our
  <a href="{{ site.data.sponsors.sponsorship_kit_url }}">sponsorship kit</a>
  and contact sponsors@bsidessf.org for more information.</h3>

{% for class in site.data.sponsors.levels %}

  <hr style="margin-bottom: 5px">
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
            <h1>{{ sponsor.type }}</h1>
          {% endif %}
          {% if sponsor.name == "Could Be You!" %}
            <a href="{{ site.data.sponsors.sponsorship_kit_url }}" target="_blank">
          {% else %}
            <a href="{{ sponsor.href }}" target="_blank">
          {% endif %}
            <div class="imgdiv">
              {% if sponsor.icon %}
                <img src="{{ site.url }}{{ sponsor.icon }}" alt="{{ sponsor.name }}" />
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

<hr style="margin-bottom: 5px">

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
