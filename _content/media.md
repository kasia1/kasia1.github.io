---
title: Media
group: navigation
order: 300
scripts: expand_collapse_toggle
---
<!--
    Changes below this line are only necessary to change display of publications,
    edit _data/media.yml to add/change content
 -->
<div class="articles" markdown="0">
{% assign article_list = site.data.media.articles | sort: 'date' | reverse %}
{% for parent_article in article_list %}
    <ul class="article">
        {% include article article=parent_article %}
        {% if parent_article.articles %}
        <li class="children">
            <ul class="showhide">
                <!-- Use this to show/hide -->
                <li>
                    <a class="toggle" href="#!">
                        <span class="glyphicon glyphicon-chevron-down"></span>&nbsp;Articles
                    </a>
                </li>
                <li class="content">
                    <ul class="children">
                    {% for child_article in parent_article.articles %}
                        <li><ul class="article">{% include article article=child_article %}</ul></li>
                    {% endfor %}
                    </ul>
                </li>
            </ul>
        </li>
        {% endif %}
    </ul>
{% endfor %}
</div>

