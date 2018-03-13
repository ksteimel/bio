---
layout: default
---
My name is Kenneth Steimel and I a Computational Linguistics student at Indiana University. You can read more about me, if you want, [here](bio.html)

My current CV can be found on [this page](curriculum-vitae.pdf)
## Intrests:

[High Performance Computing](https://hpnlp.org)

[Natural Language Processing](projects.html)

[Coffee Roasting](coffee.html)

[Homelabbing](machines.html)

## Blog posts:
{% for post in site.posts %}
   ___
   {% include post_block.html %}
   ___
{% endfor %}
