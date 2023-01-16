---
layout: ../../layouts/MarkdownPostLayout.astro
title: 'Apache und node auf uberspace Servern konfigurieren'
date: "2022-01-16"
description: ""
---

# Apache & node auf uberspace Servern konfigurieren

Im home Verzeichnis liegt die /my-node-app/…
Im apache root /html/… liegen die php files

Node Applikation starten
Daemon anlegen: (https://manual.uberspace.de/lang-nodejs/)

```
[program:my-node-app]
directory=/home/friebe/my-node-app
command=yarn run start
startsecs = 20
stopasgroup=true
stopsignal=QUIT
environment=NODE_ENV=production
```

Daemon einlesen und aktualisieren mit
supervisorctl reread my-daemon
supervisorctl update my-daemon

Node Applikation von außerhalb per URL verfügbar machen mit webbackend (https://manual.uberspace.de/web-backends/)

`Wichtig dein Node Server darf nicht auf 127.0.01 oder localhost spawnen.  Bsp 127.0.02`

Ports verknüpfen
uberspace web backend set / --http --port 3000
(Gleicher port wie dein node server)

PHP apache auf eine andere domain legen. Bsp
Api.friebe.uber.space

Subdomain anlegen
uberspace web domain add api.friebe.uber.space

Apache auf diese domain legen
uberspace web backend set api.friebe.uber.space —apache