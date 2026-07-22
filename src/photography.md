---
layout: base.njk
title: Photography
permalink: /photography/
photos:
  - src: /images/photography/0F649D61-908A-406B-926A-32EFCFB993C8.jpeg
    caption: ""
  - src: /images/photography/1173B71D-F90F-4F4A-A466-F7488D0FF74D.jpeg
    caption: ""
  - src: /images/photography/396DE905-981A-4B43-BB99-840ED256BAD5.jpeg
    caption: ""
  - src: /images/photography/73828FEC-3F8F-45CC-893C-394D2895BB07.jpeg
    caption: ""
  - src: /images/photography/954DF7BA-632D-4327-884E-AAE797D35761.jpeg
    caption: ""
  - src: /images/photography/A04C3A31-5FAF-456C-88D9-DB0094316346.jpeg
    caption: ""
  - src: /images/photography/B3A1DF8B-1A76-4912-9F12-0098A8B0C974.jpeg
    caption: ""
  - src: /images/photography/CC7A5A02-13EE-4AC2-9B31-4E8FE2734153.jpeg
    caption: ""
  - src: /images/photography/D6360F05-D156-45D4-B65A-E413BCC6256F.jpeg
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
