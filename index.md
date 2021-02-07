---
layout: default
title: "All Episodes"
---


{% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}
{% for post in site.posts %}
<div class="text-muted">
    <span><i class="fas fa-microphone-alt"></i> Ep. {{ post.itunes_episode }}</span>
    <span><i class="fas fa-calendar-alt"></i> {{ post.date | date: date_format }}</span>
    <span><i class="fas fa-clock"></i> {{ post.itunes_duration_seconds | divided_by: 60.0 | round: 1 }} minutes</span>
</div>
<h2>
    <a class="post-link" href="{{ post.url | relative_url }}">
        {{ post.title | escape }}
    </a>
</h2>
{{ post.excerpt }}

{% endfor %}

