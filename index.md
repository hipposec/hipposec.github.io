---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default 
title: "Security Wanderings"
---
I'll be using this space to write my thoughts on cyber security and any other hobbies. As I've had a couple of other websites, I'll be migrating old posts from there to here.


{% for post in site.posts limit: 10 %}
  <article class="index-page">
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
	<h4>{{ post.date | date: "%a, %b %d, %y" }}</h4>
    {{ post.excerpt }}
  </article>
{% endfor %}
