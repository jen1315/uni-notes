---
layout: default
---

# uni-notes
University notes published in a Page.

{% for page in site.pages %}

[{{ page.title }}]({{ page.url | relative_url }})

{% endfor %}