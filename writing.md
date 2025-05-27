---
layout: default
title: writing
permalink: /writing/
---

<h1> </h1>
<div class="container-fluid">

  {% if site.posts.size > 0 %}
    {% for post in site.posts %}
      <hr>
      <div class="row writing-entry">
        <div class="col-md-6">
          <h5><a href="{{ post.url }}" class="writing-title">{{ post.title }}</a></h5>
          <h6 class="writing-meta">{{ post.date | date: "%B %d, %Y" }} | {{ post.author }}</h6>
          <p>{{ post.content | markdownify }}</p>
        </div>
      </div>
    {% endfor %}
  {% else %}
    <p>No writing posts available.</p>
  {% endif %}

  <!-- caveat -->
  <div class="row">
  <div class="col-md-6">
    <p style="font-size: 15px; color: gray; margin-top: 100px;">
      *Personal opinions only; not representative of my employer
    </p>
  </div>
</div>

</div>
