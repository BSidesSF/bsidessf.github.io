---
layout: page
title: Friends of BSidesSF 2026
---

{% assign cols = 4 %}

<center>
<p>BSidesSF thanks all of its friends.<br/>
These individuals and organizations have specially donated to help make BSidesSF 2026 possible!
</p>
</center>

<hr style="margin-bottom: 5px" />
<div style="text-align: center" class="friends {{ class.class }}">
<center>
  <h2> <b>Sapphire </b></h2>
</center>

<div style="text-align: center" class="friends {{ class.class }}">
  {% assign friends_by_name = site.data.friends.sapphire %}
  {% for friend in friends_by_name %} 
    {% assign mod = forloop.index | modulo: cols %} 
    {% if mod == 1 %}
    <div class="friends row">
    {% endif %}
      <div class="friends column">
        <p>
        {% if friend.url %}
          <a href="{{friend.url}}" target=_blank >{{ friend.name }}</a>
        {% else %}
          {{ friend.name }}
        {% endif %}
        </p>
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
<div style="text-align: center" class="friends {{ class.class }}">
<center>
  <h3><b> Emerald </b></h3> 
</center>

<div style="text-align: center" class="friends {{ class.class }}">
  {% assign friends_by_name = site.data.friends.emerald %}
  {% for friend in friends_by_name %} 
    {% assign mod = forloop.index | modulo: cols %} 
    {% if mod == 1 %}
    <div class="friends row">
    {% endif %}
      <div class="friends column">
        <p>
        {% if friend.url %}
          <a href="{{friend.url}}" target=_blank >{{ friend.name }}</a>
        {% else %}
          {{ friend.name }}
        {% endif %}
        </p>
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
<div style="text-align: center" class="friends {{ class.class }}">
<center>
  <h3><b> Ruby </b></h3>
</center>

<div style="text-align: center" class="friends {{ class.class }}">
  {% assign friends_by_name = site.data.friends.ruby %}
  {% for friend in friends_by_name %} 
    {% assign mod = forloop.index | modulo: cols %} 
    {% if mod == 1 %}
    <div class="friends row">
    {% endif %}
      <div class="friends column">
        <p>
        {% if friend.url %}
          <a href="{{friend.url}}" target=_blank >{{ friend.name }}</a>
        {% else %}
          {{ friend.name }}
        {% endif %}
        </p>
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
    Want to show your support for BSidesSF? Become a Friend of BSidesSF for a limited-edition badge with t-shirt.
    <br />Purchase your <a href="/tickets">ticket</a> today!
  </p>
  <p>
    <br/>Interested in sponsoring in a larger capacity?
    <br/>Check out the <a href="/sponsors">Sponsors page</a> or contact <a href="mailto:sponsors@bsidessf.org">sponsors@bsidessf.org</a> for more information.
  </p>
</center>
