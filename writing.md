---
layout: default
title: Writing
body_class: writing-page
permalink: /writing/
---

<div class="writing-container">

  <h1 class="writing-page-title">Writing</h1>

  <ul class="writing-index-list">
    {% for post in site.posts %}
      <li class="writing-index-item">
        <h2 class="writing-index-title">
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h2>
        <p class="writing-index-date">{{ post.date | date: "%B %d, %Y" }}</p>
        <p class="writing-index-excerpt">
          {{ post.excerpt | strip_html | truncate: 400 }}
        </p>
      </li>
    {% endfor %}
  </ul>

</div>
