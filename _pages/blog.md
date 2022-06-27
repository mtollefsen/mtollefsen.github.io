---
title:  "Blog"
layout: posts
classes: wide
header:
  overlay_image: /assets/images/BLANK.jpg
permalink: /blog/
author_profile: true
comments: false
---

{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor%}
