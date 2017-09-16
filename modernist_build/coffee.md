---
layout: default
title: Coffee Roasting Posts
category_name: coffee
---
# My roaster

I have a Freshroast SR 500 air roaster that I use extremely often. It holds about 3.5 oz of green coffee beans which then float on a bed of extremely hot air until roasted. This roaster allows me to modify the heat of the air as well as the speed of the fans. Higher fan speed also lowers the effect the temperature has since the air is not in contact with the beans for as long. 

Originally, I turned to roasting because it was much more cost effective where I live (especially considering the cost of electricity). However, now I am more engaged with the challenge of making decent coffee in my home. It takes practice and patience to get the right roasting settings but I enjoy this.

# Blog posts about Coffee


{% if page.category_name %}
   {%assign category_name = page.category_name %}
{% endif %}


{% for post in site.categories[category_name] %}
  ___
  {% include post_block.html %}
  ___
{% endfor %}
