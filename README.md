# ethos-server-websocket

## Sending surveys to clients

Run the command `pm2 sendSignal SIGUSR1 ethos-server-websocket` to prompt the clients to display heat survey

## Installation & running

Requirements: _npm and pm2 to be installed_

1. Run `npm install` to install required dependencies
2. Run `pm2 start pm2.config.js` to start server running with pm2
3. Run `pm2 save` to save pm2 configuration
4. Run `pm2 startup` and configure pm2 to launch on startup
5. Configure NGINX (if required)

## NGINX config

```nginx
location /ws/ {
  proxy_pass http://localhost:8080;
  proxy_http_version 1.1;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "Upgrade";
  proxy_set_header Host $host;
}
```
