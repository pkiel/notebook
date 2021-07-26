---
layout: page
permalink: /categories/
title: Posts by Categories
---

<h3 class="category-head">Navigate to a Category</h3>
<p>
	{% for category in site.categories %}
	{% capture category_name %}{{ category | first }}{% endcapture %}
		<a href="#{{}category_name}"> {{ category_name }} ({{ site.categories[category_name].size }}) </a> / 
	{% endfor %}
</p>
<hr />
<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <h3 class="category-head">{{ category_name }} ({{ site.categories[category_name].size }})</h3>
    {% for post in site.categories[category_name] %}
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a> {% if post.date %} - {{ post.date | date: "%m/%d/%Y" }}{% endif %}</h4>
    {% endfor %}
  </div>
{% endfor %}
</div>

