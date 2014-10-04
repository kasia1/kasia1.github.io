---
title: Publications
group: navigation
order: 200
---
Or find me on [Google][google] and [PubMed][pubmed]

[google]: http://scholar.google.com/citations?user=wFAq3OMAAAAJ&hl=en&oi=ao
[pubmed]: http://www.ncbi.nlm.nih.gov/pubmed/?term=bryc+k%5Bau%5D


    {% for paper in site.data.cv.publications %}
        {% capture strftime %}
            {% if paper.date.strftime %}
                {{ paper.date.strftime }}
            {% else %}
                %Y %b %-d
            {% endif %}
        {% endcapture %}
        {% capture pub_date %}
            {% if paper.date.value %}
                {{ paper.date.value }}
            {% else %}
                {{ paper.date }}
            {% endif %}
        {% endcapture %}
<div class="citation">
        <ul>
            <li class="title">{{ paper.title }}</li>
            <li class="authors">
                <ul>
                    {% for author in paper.authors %}
                        {% if author.person.email == site.author.email %}
                            <li><strong>{{ author.name }}</strong></li>
                        {% else %}
                            <li>{{ author.name }}</li>
                        {% endif %}
                    {% endfor %}
                </ul>
            </li>
            <li class="journal">{{ paper.journal.name }}</li>
            <li class="date">{{ pub_date | date: strftime }}</li>
        </ul>
</div>
{{ paper.abstract }}

    {% endfor %}
