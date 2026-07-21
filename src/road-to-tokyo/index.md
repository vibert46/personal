---
layout: base.njk
title: Road to Tokyo
permalink: /road-to-tokyo/
---

<h1 class="page-title">Road to Tokyo</h1>

<div class="prose">

In April 2025, we quit our jobs, sold all our stuff, bought a motorcycle, and rode it from Jersey (UK) to Japan. Over 6 months, we travelled through 25 countries and over 35,000km.
<iframe src="https://www.google.com/maps/d/u/0/embed?mid=13Q3BJrrkCm77-YGinOScVNHQONU3udA&ehbc=2E312F&noprof=1" width="640" height="480"></iframe>

</div>

<ul class="post-list">
  {% for post in collections.tokyoPosts %}
  <li>
    <a class="post-title" href="{{ post.url }}">{{ post.data.title }}</a>
    <span class="post-date">{{ post.data.date | readableDate }}{% if post.data.distance %} · {{ post.data.distance }}{% endif %}</span>
  </li>
  {% endfor %}
</ul>
