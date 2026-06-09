---
layout: default
title: Writing
body_class: writing-page
permalink: /writing/
---

<div class="writing-container">

  <h1 class="writing-page-title">Writing</h1>

  <hr>

  <ul class="writing-index-list">
    {% for post in site.posts %}
      <li class="writing-index-item">


    <h2 class="writing-index-title">
      <a href="{{ post.url }}">{{ post.title }}</a>
    </h2>

    <p class="writing-index-date">
      {{ post.date | date: "%B %d, %Y" }}
    </p>

    <p class="writing-index-excerpt">
      {{ post.content | strip_html | truncatewords: 120 }}
    </p>

    <a href="{{ post.url }}" class="keep-reading-btn">
      Keep reading →
    </a>

  </li>

  <hr>

{% endfor %}


  </ul>

  <div class="writing-disclaimer">
    Opinions expressed here are my own and do not necessarily reflect the views
    of any employer, institution, or organization with which I am affiliated.
  </div>

</div>
