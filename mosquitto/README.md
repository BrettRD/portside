# Mosquitto

This config uses nginx-proxy and le-companion to negotiate SSL certificates and run SSL offloading on websockets connections and HTTP pages.

Mosquitto will access the SSL certificates directly to serve encrypted MQTT.

* put your domain name in `.env`
* select the matching certificate for mqtt over ssl under `config/conf.d/ssl_8883.conf` and uncomment the rest
* `sudo docker-compose up -d`


It'll probably fail the first time while le-companion negotiates a cert from Lets Encrypt, wait a minute and try again.

Mosquitto may need to cop a reload signal every couple of months to reload the certs.  Under a native install, there would be a post-cert-update callback to reload anything that uses the certs. 