# Eduflow Deploy Repository
This repository lets you deploy everything with one command, automatically sets up https using caddy.

## Starting
Run the following to start all services:
`sudo docker compose up`

To start it in detached mode:
`sudo docker compose up -d`

(requires root, because it uses port 80 and 443)

## Configuring the URL

We have to differentiate between two URLs:

 - frontend-url (default: https://localhost)
 - backend-url (default: https://api.localhost)

You can change those URLs in the .env file, which is self explanatory. (replace every occurence of localhost with your own domain)

If you also would like to change the ports, you have to add them only to the FRONTEND_CORS_URL and BACKEND_URL variable, additionally you have to change the ports (the ports before the colon x:80 and x:443 (change the x)) in the compose file in the caddy section. 

WARNING: changing the ports will break the automatic redirect from http to https (as you will be automatically redirected to :443 which you just changed)