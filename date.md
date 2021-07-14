---
layout: page
permalink: /datearchive/
title: Posts by Date
---

<div id="date_archives">
{% for post in site.posts %}
  {% assign currentdate = post.date | date: "%B %Y" %}
  {% if currentdate != date %}
    {% unless forloop.first %}</ul>{% endunless %}
    <h1 id="y{{post.date | date: "%B %Y"}}">{{ currentdate }}</h1>
    <ul>
    {% assign date = currentdate %}
  {% endif %}
    <li><a href="{{ post.url }}">{{ post.title }}</a> {% if post.date %} - {{ post.date | date: "%m/%d/%Y" }}{% endif %} </li>
  {% if forloop.last %}</ul>{% endif %}
{% endfor %}
</div>

