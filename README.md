{% assign mydocs = site.blog_posts | group_by: 'category' %}
{% for cat in mydocs %}
<h2>{{ cat.name }}</h2>
    {% assign docs = cat.items | sort: 'published' | reverse %}
    {% for doc in docs %}
        <h3><a href="{{ doc.url }}">{{ doc.title }}</a></h2>
        {{ doc.description }}<br/>
        <i>Published: {{ doc.published }}</i>
    {% endfor %}
</ul>
{% endfor %}

