# uni-notes
University notes published in a Page.

{% for page in site.pages %}

[{{ page.title }}]({{ page.url }})

{% endfor %}
