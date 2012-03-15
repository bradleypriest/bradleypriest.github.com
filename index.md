---
layout: home
title: Home
tagline:
---
{% include JB/setup %}
{% for post in site.posts limit:2 %}
  <article>
      <h2>
        <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
        <small>{{ post.date | date_to_string }}</small>
      </h2>
    <div class='post-content'>
      {{ post.content }}
    </div>
    <a href="{{ BASE_PATH }}{{ post.url }}#disqus_thread" {% if post.guid %}data-disqus-identifier='{{post.guid}}'{%endif%}>Comments</a>
  </article>
{% endfor %}