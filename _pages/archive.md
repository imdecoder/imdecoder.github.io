---
title: Archive
permalink: /archive/
---

<section class="page__content">
{% for post in site.posts %}
    {% capture year %}{{ post.date | date:"%Y" }}{% endcapture %}
    {% if year != currentYear %}
        {% assign currentYear = year %}
        <p>{{ currentYear }}</p>
    {% endif %}
    <p class="archive__item-title">
        <time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time> 
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </p>
{% endfor %}
</section>
