---
layout: default
---
<!-- <p>
    <ul>
        {% for post in site.posts %}
            {% unless post.draft %} 
                <li><em>{{ post.date | date: "%a, %b %d, %Y" }}</em> <a href="{{ post.url }}">{{ post.title }}</a></li>
            {% endunless %} 
        {% endfor %}
    </ul>
</p> -->

<div class="posts">
  {% for post in site.posts %}
  <div class="post">
    <h1 class="post-title">
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h1>

    <span class="post-date">{{ post.date | date_to_string }}</span>

  </div>
  {% endfor %}
</div>