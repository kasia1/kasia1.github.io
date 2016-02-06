---
title: Publications
group: navigation
order: 200
scripts: [ altmetric, expand_collapse_toggle ]
---
Or find me on [Google][google] and [PubMed][pubmed]

[google]: http://scholar.google.com/citations?user=wFAq3OMAAAAJ&hl=en&oi=ao
[pubmed]: http://www.ncbi.nlm.nih.gov/pubmed/?term=bryc+k%5Bau%5D


<!--
    Changes below this line are only necessary to change display of publications,
    edit _data/cv.yml to add/change content
 -->
<div class="publications" markdown="0">
{% assign publication_list = site.data.cv.publications | sort: 'date' | reverse %}
{% for paper in publication_list %}
    {% capture strftime %}
        {% if paper.strftime %}
            {{ paper.strftime }}
        {% else %}
            %Y %b %-d
        {% endif %}
    {% endcapture %}

    {% assign prev_pub_date = pub_date %}
    {% assign pub_date = paper.date %}
    {% capture pub_date_year %}{{ pub_date | date: '%Y' }}{% endcapture %}
    {% capture prev_pub_date_year %}{{ prev_pub_date | date: '%Y' }}{% endcapture %}

    {% if forloop.first %}
        <div class="year"><h3>{{ pub_date_year }}</h3>
    {% else %}
        {% if pub_date_year != prev_pub_date_year %}
        </div>
        <div class="year"><h3>{{ pub_date_year }}</h3>
        {% endif %}
    {% endif %}

            <div class="citation" id="{{ paper.index }}">
                <ul>
                    <li class="title">{{ paper.title }}</li>
                </ul>
                <ul class="authors">
                    {% for author in paper.authors %}
                        {% if author.person.email == site.author.email %}
                            <li><strong>{{ author.name }}</strong></li>
                        {% else %}
                            <li>{{ author.name }}</li>
                        {% endif %}
                    {% endfor %}
                </ul>
                <ul>
                    <li class="journal">{{ paper.journal.name }}</li>
                    <li class="date">{{ pub_date | date: strftime }}</li>
                    {% for link in paper.urls %}
                        <li>[<a href="{{ link.url }}">{{ link.label }}</a>]</li>
                    {% endfor %}
                    <li>{% include altmetric_badge doi=paper.doi date=pub_date %}</li>
                </ul>
                {% if paper.abstract %}
                <ul class="abstract">
                    <!-- Use this to show/hide -->
                    <li>
                        <a class="toggle" href="#!">
                            <span class="glyphicon glyphicon-chevron-down"></span>&nbsp;Abstract
                        </a>
                    </li>
<!-- Must be left-aligned (no preceding whitespace) for Kramdown parser -->
<li class="content"  markdown="1">
{{ paper.abstract }}
</li>
                </ul>
                {% endif %}

            </div>

    {% if forloop.last %}
        </div>
    {% endif %}
{% endfor %}
</div>
