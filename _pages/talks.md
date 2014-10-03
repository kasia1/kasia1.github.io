---
title: Past invited talks, presentations, and lectures

---
{% assign nodes = site.talks | sort: 'date' | reverse %}
{% for node in nodes %}
<div class="title">{{ node.title }}</div>
{{ node.content }}
{% endfor %}