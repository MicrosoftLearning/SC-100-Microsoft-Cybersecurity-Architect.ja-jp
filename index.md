---
title: オンラインでホスティングされている手順
permalink: index.html
layout: home
---

# コンテンツ ディレクトリ

各ケース スタディへのハイパーリンクを次に示します。


## 2023 年 5 月のコンテンツ更新に合わせて再編成されたケース スタディ

{% assign casestudy= site.pages | where_exp:"page", "page.url contains '/Instructions/CaseStudyv2/'" %}
| モジュール | ケース スタディ |
| --- | --- | 
{% for activity in casestudy  %}| {{ activity.casestudy.module }} | [{{ activity.casestudy.title }}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}


## 以前のケース スタディの編成

{% assign casestudy= site.pages | where_exp:"page", "page.url contains '/Instructions/CaseStudy/'" %}
| モジュール | ケース スタディ |
| --- | --- | 
{% for activity in casestudy  %}| {{ activity.casestudy.module }} | [{{ activity.casestudy.title }}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}