---
layout: page
title: Research Blog
permalink: /blog/
---

<div class="docs-section">
  <div class="blog-header">
    <p class="lead">My goal is to share implementations of the work I have been reading. I hope to break down these papers into simple and digestible content.</p>
    <h5 style="margin-top: 1.5rem;"><b>Recent Posts</b></h5>
  </div>

  {% assign sorted_posts = site.posts | sort: "date" | reverse %}
  {% for post in sorted_posts %}
  <div class="blog-post">
      <h5>
        <a href="{{ post.url }}" style="color: #222; text-decoration: none;">{{ post.title }}</a>
      </h5>

      <div class="post-meta" style="color: rgba(0, 0, 0, 0.6); margin-bottom: 15px;">
        <span style="font-weight: 600;">{{ post.date | date: "%B %d, %Y" }}</span>
        {% if post.tags %}
          <span>
            |
            {% for tag in post.tags %}
              <a href="{{ site.baseurl }}/tags/{{ tag | slugify }}/" style="color: #666; text-decoration: none; font-size: 1rem;">{{ tag }}</a>
              {% unless forloop.last %}, {% endunless %}
            {% endfor %}
          </span>
        {% endif %}
      </div>

      <div class="post-excerpt" style="line-height: 1.6; color: rgba(0, 0, 0, 0.8);">
        {% if post.excerpt %}
          {{ post.excerpt | strip_html | truncatewords: 40 }}
        {% else %}
          {{ post.content | strip_html | truncatewords: 40 }}
        {% endif %}
        <a href="{{ post.url }}" style="color: #33C3F0; text-decoration: none; font-weight: 600;">Read more →</a>
      </div>
    </div>
    {% endfor %}

    {% if site.posts.size == 0 %}
    <div style="text-align: center; padding: 60px 0; color: rgba(0, 0, 0, 0.6);">
      <p>No blog posts yet. Check back soon!</p>
    </div>
    {% endif %}
</div>