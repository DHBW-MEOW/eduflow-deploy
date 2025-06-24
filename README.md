# Eduflow Deploy Repository
This repository lets you deploy everything with one command, automatically sets up https using caddy.

## Starting
Very simple, just run:
`docker compose up`

To start it in detached mode:
`docker compose up -d`

## Configurating
Changing the URLs on which the server is running:

We have to differentiate between two URLs:

 - frontend-url (default: https://localhost)
 - backend-url (default: https://api.localhost)

The frontend url is used by the user, this is where the website is accessed.

The backend url is used by the frontend, in order to send request to the backend.

Technically speaking you could use two completely different URLs for both of them, however it is recommended to use https://api.\[frontend-url\] as backend URL.

The following locations need to be modified if changing the URL:

Inside api_endpoint.txt: here the full backend-url is required (e.g. https://api.localhost) it is read by the frontend.

Inside compose.yaml: In the backend section the env-variable FRONTEND_CORS_URL has to be set to the frontend-url, it is read by the backend and configures CORS.

Inside Caddyfile: Here you can set the frontend and backend-url individually, this is used by the reverse proxy and determines the URLs.