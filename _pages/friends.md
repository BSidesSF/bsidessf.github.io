---
layout: page
title: Friends of BSidesSF 2024
---
{% assign cols = 4 %}


<hr style="margin-bottom: 5px" />
<div style="text-align: center" class="friends {{ class.class }}">
<center>
  <p>BSidesSF thanks the following organizations and individuals who have donated $300 or more to help make BSidesSF 2024 possible!</p>
</center>
{% assign orgs_by_name = site.data.friends.orgs %}
{% for org in orgs_by_name  %}
    {% assign mod = forloop.index | modulo: cols %}
      {% if mod == 1 %}
      <div class="friends row">
      {% endif %}
        <div class="friends column">
          <a href="{{org.link}}" target="_{{org.name}}" rel="noopener noreferrer">
            <p>{{ org.name }}</p>
          </a>
        </div>
      {% if mod == 0 %}
      </div>
      {% endif %}
    {% if mod == 0 %}
    </div>
    {% endif %}
{% endfor %}
</div>

<div style="text-align: center" class="friends {{ class.class }}">
  {% assign friends_by_name = site.data.friends.people %}
  {% for friend in friends_by_name %} 
    {% assign mod = forloop.index | modulo: cols %} 
    {% if mod == 1 %}
    <div class="friends row">
    {% endif %}
      <div class="friends column">
         <p>{{ friend.name }}</p>
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
    Want to become a Friend of BSidesSF? Purchase your <a href="/tickets">ticket</a> today!
    <br/>Interested in sponsoring in a larger capacity?
    <br/>Check out the <a href="{{ site.data.sponsors.sponsorship_kit_url }}">sponsorship kit</a>
    <br/>or contact <a href="mailto:sponsors@bsidessf.org">sponsors@bsidessf.org</a>.
  </p>
</center>
