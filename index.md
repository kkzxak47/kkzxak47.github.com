---
layout: page
title: ZhongXun's
tagline: place to speak mind
---
{% include JB/setup %}

<h3>Post List:</h3>

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


