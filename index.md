---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default 
title: "My Notes"
---
Random collection of ideas on cybersec, astronomy, ham radio and whatever was interesting at the time.<br>
<a href="/about.html">About Me</a><br>
<a rel="me" href="https://infosec.exchange/@hipposec2">Mastodon</a>

{% for post in site.posts limit: 10 %}
  <article class="index-page">
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
	<h4>{{ post.date | date: "%a, %b %d, %y" }}</h4>
    {{ post.excerpt }}
  </article>
{% endfor %}
