#SSL gateway

This is a fairly plain example of the nginx-proxy and the le-companion to run ssl over a collection of services

Lets Encrypt might need to send you emails regarding misconfiguration, add your email address in .env

nginx.tmpl is unmodified from the nginx-proxy instructions, and only included for completeness.

You need to 'docker create volume' for 'ssl-gateway-conf', 'ssl-gateway-vhost', 'ssl-gateway-html', and 'ssl-gateway-certs'.
Mosquitto will access its certs directly to avoid configuring mqtt pass-through on nginx-proxy.
