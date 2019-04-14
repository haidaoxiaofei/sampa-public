---
layout: default
title: Research Projects
projects:
  - link: approximation/
    name: Approximate Computing
    summary: Approximation will never work.
  - link: dmp.html
    name: Deterministic Parallelism
    summary: Determinism is inevitable.
---

Our research explores research related to spatial-temporal information and general crowdsourcing, from algorithms design to applications development. Our research has three main themes. The *task assignment* theme addresses challenges in batch-based matching of workers and tasks in various demond-supply systems, such as spatial crowdsourcing systems, public resource allocation systems and so on. The *general crowdsourcing* theme focuses on latency control, copying detecton and training data preparation in general crowdsourcing systems. The *smart transportation* theme aims at taking advantage of huge data collected by morden online dial-a-ride systems and the novel minng/learning methods to discover and predict the trends of travelers such that the efficiency of the public transportation and user experience can be improved. 


<div class="card-columns">
{% for p in site.projects %}
{% if p.status != "inactive" %}
<div class="card {%if p.link or p.url%}link{%endif%}">
    {% if p.link %}
        {% assign proj_url = p.link %}
    {% else %}
        {% capture proj_url %}{{site.base}}{{p.url}}.html{% endcapture %}
    {% endif %}
    
    <a href="{{proj_url}}">
        <div class="card-block">
            <div class="title">
                {% if p.image %}
                    {% assign imgurl = p.image %}
                    {% capture init %}{{ p.image | slice: 0,1 }}{% endcapture %}
                    {% if init == "/" %}
                        {% capture imgurl %}{{site.base}}{{p.image}}{% endcapture %}
                    {% endif %}
                    <h3 class="card-title">
                        <img class="icon img-responsive" src="{{imgurl}}" alt="{{p.title}}"/>
                    </h3>
                {% endif %}                
                <h3 class="card-title">{{p.title}}</h3>
            </div>
            <div class="card-text">
                {{ p.description | markdownify }}
            </div>
        </div>
        {% if p.people %}
        <div class="card-footer">
            {% include project-people.html people=p.people %}
        </div>
        {% endif %}
    </a>
</div>
{% endif %}
{% endfor %}
</div>




{% include footer.html %}

