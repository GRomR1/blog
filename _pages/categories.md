---
layout: archive
permalink: /categories/
title: "Categories"
author_profile: true
---

{% include group-by-array collection=site.posts field="categories" %}
<ul>
{% for category in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <a href='{{ category | slugify }}'><h2 id="{{ category | slugify }}" class="archive__subtitle">{{ category }}</h2>
  </a>
  {% for post in posts %}

    <li>
      <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </li>

  {% endfor %}
{% endfor %}
</ul>


<h1>Tags</h1>
<div>
  <p style="text-align: justify;">
{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}{% assign tags = site_tags | split:',' | sort %}
{% include tagcloud.html %}
  </p>
</div>
