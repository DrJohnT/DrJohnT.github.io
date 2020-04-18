# Welcome to Dr John's Blog

## Home Automation 
{% for doc in site.blog_posts %}
<ul>  
    {% if doc.category == "home-automation" %}
        <li><b><a href="{{ doc.url }}">{{ doc.title }} ({{ doc.published }})</a></b><br/>{{ doc.description }}
        </li>
    {% endif %}
</ul>
{% endfor %}

## DevOps 

## Business Intelligence
