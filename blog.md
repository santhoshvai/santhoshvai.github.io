---
layout: page
title: blog
---
<div class="blog">
  <!-- <h2>Totally {{ site.posts | size }} posts!</h2> -->
  <ul class="blog-posts">
    {% for post in site.posts %}
      <li>
        <h2>
          <a href="{{ post.url }}">
            {{ post.title }}
          </a>
      </h2>
      <time datetime="{{ post.date | date_to_string }}"> <small>{{ post.date | date_to_string }}</small></time>
      </li>
    {% endfor %}
  </ul>
</div>
