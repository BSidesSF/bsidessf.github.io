---
layout: page
title: "Past Events"
---

<ul class="no-marker">
{% for hist in site.data.history %}
  <li class="past-event">
  <h2 class="pe-year">{{ hist.year }}</h2>
  <ul class="column-3 no-marker" >
    <li> 
      {% if hist.archived_site and hist.archived_site != "" %}
        <a href="{{ hist.archived_site }}">Website</a> 
      {% else %} &nbsp; 
      {% endif %}
    </li>
    <li> 
      {% if hist.program_docid and hist.program_docid != "" %}
        <a href="https://drive.google.com/open?id={{ hist.program_docid }}" target=_blank>Program (external)</a> 
      {% else %}&nbsp;
      {% endif %}
    </li>
    <li> 
      {% if hist.sched_id and hist.sched_id != "" %}
        <a href="https://{{ hist.sched_id }}.sched.com" target="_blank">Schedule (external)</a> 
      {% else %}&nbsp;
      {% endif %}
    </li>
    <li> 
      {% if hist.youtube_playlist_id and hist.youtube_playlist_id != "" %}
        <a href="https://www.youtube.com/playlist?list={{ hist.youtube_playlist_id }}" target=_blank>Youtube Playlist (external)</a> 
      {% else %}&nbsp;
      {% endif %}
    </li>
    <li> 
      {% if hist.sponsorship_kit_id and hist.sponsorship_kit_id != "" %}
        <a href="https://drive.google.com/open?id={{ hist.sponsorship_kit_id }}" target=_blank>Sponsorship Kit (external)</a> 
      {% else %}&nbsp;
      {% endif %}
    </li>
    <li> 
      {% if hist.closing_ceremony_docid and hist.closing_ceremony_docid != "" %}
        <a href="https://drive.google.com/open?id={{ hist.closing_ceremony_docid }}" target=_blank>Closing Ceremony Slides (external)</a> 
      {% else %}&nbsp;
      {% endif %}
    </li>
    <li> 
      {% if hist.bsides_wiki and hist.bsides_wiki != "" %}
        <a href="{{ hist.bsides_wiki }}" target=_blank>Security BSides Wiki (external)</a> 
      {% else %}&nbsp;
      {% endif %}
    </li>
    <li> 
      {% if hist.posters_url and hist.posters_url  != "" %} 
        <a href="{{ hist.posters_url }}">Graphic Recordings</a>
      {% else %}&nbsp;
      {% endif %}
    </li>
    {% for item in hist.others %}
    <li>
      <a href="{{ item.href }}" {% if item.external %} target="_blank" {% endif %} >
        {{ item.title }} {% if item.external %}(external){% endif %}
      </a> 
    </li>
    {% endfor %}
    </ul>
  </li>
{% endfor %}
</ul>
