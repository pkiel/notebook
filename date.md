---
layout: page
permalink: /datearchive/
title: Posts by Date
---

<div id="date_archives">
{% for post in site.posts %}
	{% unless post.next %}
		<h2 class="archivetitletopbottom">{{ post.date | date: '%Y' }}</h2>
	{% else %}
		{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}{% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
		{% if year != nyear %}
			</ul><h2 class="archivetitletopbottom">{{ post.date | date: '%Y' }}</h2>
		{% endif %}
	{% endunless %}
{% capture month %}{{ post.date | date: '%m%Y' }}{% endcapture %}
{% capture nmonth %}{{ post.next.date | date: '%m%Y' }}{% endcapture %}
{% if month != nmonth %}
	{% if forloop.index != 1 %}</ul>{% endif %}
	<h2 class="archivetitle">{{ post.date | date: '%B %Y' }}</h2><ul>
	{% endif %}
	{% if post.link %}
	<h3 class="link-post">
		<a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
		<a href="{{ post.link }}" target="_blank">
			<i class="fa fa-link"></i></a>
	</h3>
	{% else %}
		<li><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a> 
		{% if post.date %} - {{ post.date | date: "%m/%d/%Y" }}{% endif %}</li>
	{% endif %}
{% endfor %}
	</ul>
</div>

