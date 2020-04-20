{% assign mydocs = site.blog_posts | group_by: 'category' %}
{% for cat in mydocs %}
<h2>{{ cat.name }}</h2>
<div>
    {% assign docs = cat.items | sort: 'published' | reverse %}
    {% for doc in docs %}
        <a href="{{ doc.url }}">{{ doc.title }}</a>
        {{ doc.description }}<br/>
        <i>Published: {{ doc.published }}</i>
    {% endfor %}
</div>
{% endfor %}

