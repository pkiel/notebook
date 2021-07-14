---
layout: page
permalink: /monthview/
title: Posts by Date
---

<div id="archives">
{% for post in site.posts %}
{% unless post.next %}
<h2 class="archive-group">{{ post.date | date: '%Y' }}</h2>
{% else %}{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}{% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}{% if year != nyear %}</ul><h2 class="archive-group">{{ post.date | date: '%Y' }}</h2>{% endif %}{% endunless %}% capture month %}{{ post.date | date: '%m%Y' }}{% endcapture %}{% capture nmonth %}{{ post.next.date | date: '%m%Y' }}{% endcapture %}{% if month != nmonth %}{% if forloop.index != 1 %}</ul>{% endif %}<h2 class="category-head">{{ post.date | date: '%B %Y' }}</h2><ul>{% endif %}{% if post.link %}<h4 class="archive-item"><a href="{{ site.baseurl }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a><a href="{{ post.link }}" target="_blank" title="{{ post.title }}"><i class="fa fa-link"></i></a></h4>{% else %}<li><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a> {% if post.author %} • {{ post.author }}{% endif %}{% if post.date %} • {{ post.date | date: "%B %e, %Y" }}{% endif %}</li>{% endif %}{% endfor %}</ul></div>

