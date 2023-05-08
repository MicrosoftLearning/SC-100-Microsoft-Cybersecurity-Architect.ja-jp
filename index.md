---
title: Online Hosted Instructions
permalink: index.html
layout: home
---

# Content Directory

Hyperlinks to each of the lab exercises and demos are listed below.

## Labs

{% assign caseStudy = site.pages | where_exp:"page", "page.url contains '/Instructions/CaseStudy'" %}
| Module | CaseStudy |
| --- | --- | 
{% for activity in caseStudy  %}| {{ activity.caseStudy.module }} | [{{ activity.caseStudy.title }}{% if activity.caseStudy.type %} - {{ activity.caseStudy.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}


