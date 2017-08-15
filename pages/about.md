---
layout: page
title: About
description: 关于页面
keywords: GongYangbo
comments: true
menu: 关于
permalink: /about/
---


坚信熟能生巧，努力改变人生。

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
