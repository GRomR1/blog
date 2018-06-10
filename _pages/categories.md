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
  <h2 id="{{ category | slugify }}"><a href='{{ category | slugify }}' class="archive__subtitle">{{ category }}</a></h2>
  {% for post in posts %}
    <li>
      <a href="{{ post.url | prepend: site.baseurl }}" class="archive__item-title">{{ post.title }}</a>
    </li>
  {% endfor %}
{% endfor %}
</ul>

<hr />
<h1>Tags</h1>
{% include tagcloud2.html %}