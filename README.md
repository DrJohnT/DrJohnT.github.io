---
layout: default
title: Sparks from the Anvil
description: Sparks from the Anvil blog by Dr John
image: ./assets/images/sparks_from_the_anvil.png
---
{% assign mydocs = site.blog_posts | group_by: 'category' %}
{% for cat in mydocs %}
<h1>{{ cat.name }}</h1>
<div>
    {% assign docs = cat.items | sort: 'published' | reverse %}
    {% for doc in docs %}
    <h2><a href="{{ doc.url }}">{{ doc.title }}</a></h2>
    <p>{{ doc.description }}<br/>
    <small><i>Published: {{ doc.published }}</i></small>
    </p>
    {% endfor %}
</div>
{% endfor %}

