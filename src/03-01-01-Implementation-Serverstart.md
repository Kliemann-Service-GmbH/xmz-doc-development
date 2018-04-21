# Implementation: Serverstart
[Implementation: Serverstart]: #implementation-serverstart

Der Serverstart wird mit einem systemd Unit File realisiert.

[https://github.com/zzeroo/meta-xmz-mod-touch/tree/master/recipes-xmz-mod-touch/xmz-server-init](https://github.com/zzeroo/meta-xmz-mod-touch/tree/master/recipes-xmz-mod-touch/xmz-server-init)


## systemd Unit

```conf
# xmz-server.service
#
# systemd Unit für die xMZ-Plattform
#
[Unit]
Description="Server der xMZ-Platform"
After=weston.service

[Service]
Type=simple
Environment=XDG_RUNTIME_DIR=/run/user/0
Environment=XMZ_HARDWARE=0.1.0
Environment=LANG=de_DE.UTF-8
Environment="ROCKET_ENV=prod"
Environment="ROCKET_ADDRESS=127.0.0.1"
Environment="ROCKET_PORT=1337"
Environment="ROCKET_LOG=critical"
ExecStart=/usr/bin/xmz-server
Restart=always
RestartSec=10s
```
