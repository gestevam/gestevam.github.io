---
layout: default
title: Blog
permalink: /blog/
---

<h1>Blog</h1>
<div class="container-fluid">

  {% if site.posts.size > 0 %}
    {% for post in site.posts %}
      <hr>
      <div class="row blog-entry">
        <div>
          <h5><a href="{{ post.url }}" class="blog-title">{{ post.title }}</a></h5>
          <h6 class="blog-meta">{{ post.date | date: "%B %d, %Y" }} | {{ post.author }}</h6>
          <p>{{ post.excerpt }} <a href="{{ post.url }}" class="read-more">Read more...</a></p>
        </div>
      </div>
    {% endfor %}
  {% else %}
    <p>No blog posts available.</p>
  {% endif %}

</div>
