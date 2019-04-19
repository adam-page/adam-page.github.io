---
layout: default
title: Blog
permalink: /blog/
---
# {{page.title}}

## Categories

{% comment %}

The code on this page is adapted from: https://gist.github.com/Phlow/a0e3fa686eb259fe7f76

{% endcomment %}

<ul>
{% assign categories_list = site.categories %}
    {% for category in categories_list %}
      <li><a href="#{{ category[0] | downcase | url_escape | strip | replace: ' ', '-' }}">{{ category[0] | camelcase }} ({{ category[1].size }})</a></li>
    {% endfor %}
{% assign categories_list = nil %}
</ul>


{% for category in site.categories %} <h3 id="{{ category[0] | downcase | url_escape | strip | replace: ' ', '-' }}">{{ category[0] | camelcase }}</h3>
  <ul>
    {% assign pages_list = category[1] %}
    {% for post in pages_list %}
      {% if post.title != null %}
      {% if group == null or group == post.group %}
      <li><a href="{{ post.url }}">{{ post.title }} &mdash; <time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></a></li>
      {% endif %}
      {% endif %}
    {% endfor %}
    {% assign pages_list = nil %}
    {% assign group = nil %}
  </ul>

{% endfor %}