---
title: 全部文章
layout: default
permalink: /all
---
# 全部文章

{% for category in site.categories %}
{% capture category_name %}{{ category | first }}{% endcapture %}
## {{ category_name }}

{% for post in site.categories[category_name] %}
- [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}

{% endfor %}