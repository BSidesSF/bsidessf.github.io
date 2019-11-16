---
layout: page
title: "Sponsors"
---

<h3>Interested in sponsoring? Check out our
  <a href="https://drive.google.com/open?id=1atN6ykppegBe0_nBiSWAG3qeLRq8wk6w">sponsorship kit</a>
  and contact sponsors@bsidessf.org for more information.</h3>

{% for class in site.data.sponsors %}
  <hr style="margin-bottom:5px">
  <div style="text-align: center;" class="sponsors {{ class.class }}">
    <h1>{{ class.level }}</h1>
    <div class="row">
      {% for sponsor in class.sponsors %}
        <div class="column">
          <h1>{{ sponsor.type }}</h1>
          <a href="{{ sponsor.href }}" target="new">
            <img src="{{site.url}}{{sponsor.icon}}" />
          </a>
          <p><em>{{ sponsor.name }}</em></p>
        </div>
      {% endfor %}
    </div>
  </div>
{% endfor %}

<center>
  <p>
    If you have an idea for a sponsorship type you don't see listed, please reach out with your idea
  </p>
</center>
