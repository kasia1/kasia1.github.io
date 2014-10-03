---
title: Software
collection: software
---
{% assign nodes = site.software | sort: 'date' | reverse %}
{% for node in nodes %}
<p class="title">{{ node.title }}</p>
{{ node.content }}
{% endfor %}