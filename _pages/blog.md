---

title:  "Blog"
layout: archive
permalink: /Blog/
author_profile: true
comments: true

---

This is my blog page.

{% for post in site.posts limit:3 %}
  {% include archive-single.html %}
{% endfor %}