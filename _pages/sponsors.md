---
layout: page
title: "Sponsors"
---

<h3>Sponsorships are now closed. Check back soon for information on how to sponsor BSidesSF 2022.</h3>

{% for class in site.data.sponsors %}

  <hr style="margin-bottom: 5px">
  <div style="text-align: center;" class="sponsors {{ class.class }}">
    <h1>{{ class.level }}</h1>
    <div class="row">

      {% for sponsor in class.sponsors %}
        {% if sponsor.break %}
          </div><div class="row">
          {% continue %}
        {% endif %}
        <div class="column">
          <h1>{{ sponsor.type }}</h1>
          <a href="{{ sponsor.href }}" target="_blank">
            <div class="imgdiv">
              <img src="{{ site.url }}{{ sponsor.icon }}" />
            </div>
            <div>
              <p>{{ sponsor.name }}</p>
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
    <em>
      {% for class in site.data.sponsors %}
        {% for sponsor in class.sponsors %}
          {{ sponsor.credits }}
        {% endfor %}
      {% endfor %}
    </em>
  </p>
</center>
