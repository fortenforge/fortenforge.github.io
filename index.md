---
layout: page
---
{% for post in site.posts %}
  <h1 class="post-title"><a href="{{ BASE_PATH }}{{ post.url }}"> {{ post.title }} </a></h1>
  <p><span class="post-date"> {{ post.date | date: "%b %d, %Y" }} </span></p>

  <div>
  {% if post.content contains '<!--more-->' %}
    {{ post.content | split:'<!--more-->' | first }}

    <a href="{{ BASE_PATH }}{{ post.url }}"><span class="read-more">Read more...</span></a>

  {% else %}
    {{ post.content }}
  {% endif %}

  </div>

  <br />
{% endfor %}
