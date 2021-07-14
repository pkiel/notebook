---
layout: page
permalink: /date/
title: Posts by Date
---

<div id="archives">
{% for date in site.dates %}
  <div class="archive-group">
    {% capture date %}{{ date | first }}{% endcapture %}
    <div id="#{{ date | slugize }}"></div>
    <p></p>

    <h3 class="category-head">{{ date }} ({{ site.dates[date].size }})</h3>
    <a name="{{ date | slugize }}"></a>
    {% for post in site.dates[date] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %)
</div>