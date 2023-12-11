---
layout: page
title: Friends of BSidesSF 2024
---
{% assign cols = 4 %}

<script type="text/javascript" defer src="https://donorbox.org/install-popup-button.js"></script>
<a class="dbox-donation-button" style="background: #128aed url(https://donorbox.org/images/white_logo.svg) no-repeat 45px;color: #fff;text-decoration: none;font-family: Verdana,sans-serif;display: inline-block;font-size: 16px;padding: 15px 45px;padding-left: 70px;-webkit-border-radius: 8px;-moz-border-radius: 8px;border-radius: 8px;" href="https://donorbox.org/friends-of-bsidessf-2024?default_interval=o">Become a Friend of BSidesSF</a>

<p class="friends">
BSidesSF celebrates the following people and organizations
who have donated $1500 or more making BSidesSF 2024 possible!
</p>

<hr style="margin-bottom: 5px" />
<div style="text-align: center" class="friends {{ class.class }}">
  {% assign friends_by_name = site.data.friends | sort: "name" %}
  {% for friend in friends_by_name %} 
    {% assign mod = forloop.index | modulo: cols %} 
    {% if mod == 1 %}
    <div class="friends row">
    {% endif %}
      <div class="friends column">
        <a href="{{friend.link}}" target="_{{friend.name}}">
          <p>{{ friend.name }}</p>
        </a>
      </div>
    {% if mod == 0 %}
    </div>
    {% endif %} 
    {% if forloop.last and mod != 0 %}
      {% assign cnt =  mod | plus: 1 %}
      {% for i in (cnt..cols) %}
        <div class="friends column">
          <!-- column filler -->
        </div>
      {% endfor %}
    </div>
    {% endif %}
  {% endfor %}
</div>

<hr style="margin-bottom: 5px" />

<center>
  <p>
    Have further questions about becoming a Friend of BSidesSF 2024?
    <br/>See the last page of our <a href="{{ site.data.sponsors.sponsorship_kit_url }}">sponsorship kit</a>
    <br/>or contact <a href="mailto:sponsors@bsidessf.org">sponsors@bsidessf.org</a>.
  </p>
</center>
