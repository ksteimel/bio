---
title: Computational Linguistics Projects
layout: default
category: cl
---

I am a 3rd year PhD student in Computational Linguistics at Indiana University. I am interested in computational linguistics for under resourced languages, morphologically rich languages, and African languages. 

I am also interested in NLP tasks that relate to the sentiments and emotions of the author. This includes tasks like stance detection, sentiment analysis, irony/sarcasm detection etc. 


# Blog posts about computational linguistics
{% if page.category_name %}
   {%assign category_name = page.category_name %}
{% endif %}


{% for post in site.categories[category_name] %}
  ___
  {% include post_block.html %}
  ___
{% endfor %}

