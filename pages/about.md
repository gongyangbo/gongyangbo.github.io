---
layout: page
title: About
description: 关于页面
keywords: GongYangbo
comments: true
menu: 关于
permalink: /about/
---

在年轻人的颈项上，没有什么东西能比事业心这颗灿烂的宝珠更迷人的了 ——哈菲兹

## Between Heaven and Earth, every single step of ours is at full throttle, while every single road is twisting and turning. There is no constant view……

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
