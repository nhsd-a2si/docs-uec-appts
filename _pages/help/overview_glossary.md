---
title: Glossary
keywords: abbreviations, definitions, glossaries, terms
sidebar: overview_sidebar
permalink: overview_glossary.html
toc: false
---

Glossary of common terms and abbreviations used though-out the documentation.

{% for item in site.data.glossary %}  

#### {{ item.keyword }}
**{{item.expansion}}**  
{{item.definition}}

{% endfor %}
