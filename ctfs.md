---
layout: default
title: CTFs
permalink: /ctf_writeups
---

<div class="home">

  <h1 class="page-heading">CTF Writeups</h1>

  <ul class="post-list">
    {% for post in site.categories.ctfs %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h2>
      </li>
    {% endfor %}
  </ul>

</div>
