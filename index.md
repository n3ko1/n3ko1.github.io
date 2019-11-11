---
layout: page
title: Lucas Bader | n3ko1
header: 
tagline: 
---
{% include JB/setup %}
<ul>
  {% for post in site.posts %}
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
	  <h4> {{ post.tagline }}</h4>
      {{ post.excerpt }}

  <br>
	  <a class="btn btn-default btn-xs" href="{{ post.url }}">more ...</a>
  {% endfor %}
  
</ul>
