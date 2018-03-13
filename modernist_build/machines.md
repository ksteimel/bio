---

title: My infrastructure
layout: default
category_name: infrastructure

---

I have a pretty decent compute setup (given that it's pieced together on such a small budget). 

I spend most of my time on the command line on my desktop but when it comes to infrastructure beyond the level of a single computer, I still have a ton to learn. 

This is a place where I will record what I learn so that I don't forget it. Maybe someone else will think this is useful too. 

# Blog posts about computational linguistics
{% if page.category_name %}
   {%assign category_name = page.category_name %}
{% endif %}


{% for post in site.categories[category_name] %}
  ___
  {% include post_block.html %}
  ___
{% endfor %}

