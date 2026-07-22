---
layout: base.njk
title: Photography
permalink: /photography/
photos:
  - src: /images/photography/photo-01.jpg
    caption: "Replace with a caption, or delete this line"
  - src: /images/photography/photo-02.jpg
    caption: ""
  - src: /images/photography/photo-03.jpg
    caption: ""
---

<div class="photo-list">
  {% for photo in photos %}
  <div class="photo-item">
    <img src="{{ photo.src }}" alt="{{ photo.caption | default('Photograph') }}" loading="lazy">
    {% if photo.caption %}<div class="photo-caption">{{ photo.caption }}</div>{% endif %}
  </div>
  {% endfor %}
</div>
