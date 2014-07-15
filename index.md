---
layout: page
title: ZhongXun's
tagline: 
---
{% include JB/setup %}

<h3>Posts:</h3>

<ul class="posts">
  {% for post in site.posts %}
    <p><li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li></p>
  {% endfor %}
</ul>


