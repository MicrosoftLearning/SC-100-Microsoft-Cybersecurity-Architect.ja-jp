---
title: Online Hosted Instructions
permalink: index.html
layout: home
---

# Content Directory

Hyperlinks to each of the lab exercises and demos are listed below.

## Labs

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/CaseStudy'" %}
| Module | CaseStudy |
| --- | --- | 
{% for activity in CaseStudy  %}| {{ activity.CaseStudy.module }} | [{{ activity.CaseStudy.title }}{% if activity.CaseStudy.type %} - {{ activity.CaseStudy.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}


