---
title: List of posts
subtitle: These are my things
menus:
  main:
    title: My Website
    url: 'https://miguelherrero.es'
    weight: 6
layout: page
---

<p>Trying my own page</p>

<div class="post-feed">
    {% assign display_posts = '/posts' | get_pages | sort: 'date' | reverse %}
    {% for post in display_posts %}
    <article class="post post-card">
      <div class="post-card-inside">
        {% assign thumb_img_path_is_not_empty = post.thumb_img_path | is_not_empty %}
        {% if thumb_img_path_is_not_empty %}
        <a class="post-card-thumbnail" href="{{ post.url | relative_url }}">
          <img class="thumbnail" src="{{ post.thumb_img_path | relative_url }}" alt="{{ post.title }}" />
        </a>
        {% endif %}
        <div class="post-card-content">
          <header class="post-header">
            <div class="post-meta">
              <time class="published"
              datetime="{{ post.date | date: '%Y-%m-%d %H:%M' }}">{{ post.date | date: '%B %d, %Y' }}</time>
            </div>
            <h2 class="post-title"><a href="{{ post.url | relative_url }}" rel="bookmark">{{ post.title }}</a></h2>
          </header><!-- .post-header -->
          <div class="post-excerpt">
            <p>{{ post.excerpt }}</p>
            <p class="read-more">
              <a class="button inverse" href="{{ post.url | relative_url }}">Read more</a>
            </p>
          </div><!-- .post-excerpt -->
        </div><!-- .post-card-content -->
      </div><!-- .post-card-inside -->
    </article><!-- .post -->
    {% endfor %}
  </div><!-- .post-feed -->