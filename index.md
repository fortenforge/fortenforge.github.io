---
layout: page
---
{% for post in site.posts %}
  <h1 class="post-title"> {{ post.title }} </h1>
  <p><span class="post-date"> {{ post.date | date: "%b %d, %Y" }} </span></p>

  <div>
  {% if post.content contains '<!--more-->' %}
    {{ post.content | split:'<!--more-->' | first }}

  {% else %}
    {{ post.content }}
  {% endif %}

  <a href="{{ BASE_PATH }}{{ post.url }}#pi"><span class="read-more">Read more ...</span></a>
  </div>

  <br />
{% endfor %}
