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
    <h2 id="y{{post.date | date: "%B %Y"}}">{{ currentdate }}</h2>
    <ul>
    {% assign date = currentdate %}
  {% endif %}
    <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> {% if post.categories %} {% for category in site.categories %} {% capture category_name %}{{ category | first }}{% endcapture %} - <a href="/notebook/categories#{{ category_name }}">{{ category_name }}</a> {% endfor %}{% endif %} {% if post.date %} - {{ post.date | date: "%m/%d/%Y" }}{% endif %} </li>
  {% if forloop.last %}</ul>{% endif %}
{% endfor %}
</div>

