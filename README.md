{% assign mydocs = site.blog_posts | group_by: 'category' %}
{% for cat in mydocs %}
<h2>{{ cat.name }}</h2>
<ul>  
    {% assign docs = cat.items | sort: 'published' %}
    {% for doc in docs %}
        <li><a href="{{ doc.url }}"><b>{{ doc.title }}</b> (Published: {{ doc.published }})</a><br/><i>{{ doc.description }}</i></li>
    {% endfor %}
</ul>
{% endfor %}

