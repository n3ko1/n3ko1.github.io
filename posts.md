---
layout: page
title: Posts
header: 
tagline: 
group: navigation
---
{% include JB/setup %}
<ul>
  {% for post in site.posts %}
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
	  <h4> {{ post.tagline }}</h4>
      {{ post.excerpt }}

  {% unless post.tags == empty %}
    <ul class="tag_box inline">
      {% assign tags_list = post.tags %}
      {% include JB/tags_list %}
    </ul>
  {% endunless %}
  <br>
	  <a class="btn btn-default btn-xs" href="{{ post.url }}">more ...</a>
  {% endfor %}
  
</ul>