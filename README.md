{% assign mydocs = site.blog_posts | group_by: 'category' %}
{% for cat in mydocs %}
<h2>{{ cat.name }}</h2>
<div>
    {% assign docs = cat.items | sort: 'published' | reverse %}
    {% for doc in docs %}
    <h3><a href="{{ doc.url }}">{{ doc.title }}</a></h3>
    <p>{{ doc.description }}<br/>
    <small><i>Published: {{ doc.published }}</i></small>
    </p>
    {% endfor %}
</div>
{% endfor %}

