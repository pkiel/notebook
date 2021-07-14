---
layout: page
permalink: /categories/
title: Posts by Categories
---

<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>

    <h3 class="category-head">{{ category_name }} ({{ site.categories[category_name].size }})</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a> {% if post.date %} • {{ post.date | date: "%B %e, %Y" }}{% endif %}</h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>