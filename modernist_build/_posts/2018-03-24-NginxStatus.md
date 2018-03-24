---

title: Switch to Nginx
layout: default
category: infrastructure 

---

This is mostly for me to keep notes on what my status is. Maybe this will be changed into a how-to after I actually get this up and running. 

Working on installing nginx reverse proxies with ssl to enable my sharelatex instance to be accessed via the outside network without doing ssh tunneling every time. 

letsencrypt wildcard certs are not currently supported in the version of certbot that ships with ubuntu and debian.

I need to learn more about how dns subdomain verification works for ssl because wildcard certs are not absolutely necessary since I'm going to have a small number of subdomains
