# Guacamole with docker compose
This is a small documentation how to run a fully working **Apache Guacamole (incubating)** instance with docker (docker compose). The goal of this project is to make it easy to test Guacamole.

> **DO NOT USE THIS REPO for PRODUCTIVE USE!**

## About Guacamole
Apache Guacamole (incubating) is a clientless remote desktop gateway. It supports standard protocols like VNC, RDP, and SSH. It is called clientless because no plugins or client software are required. Thanks to HTML5, once Guacamole is installed on a server, all you need to access your desktops is a web browser.

It supports RDP, SSH, Telnet and VNC and is the fastest HTML5 gateway I know. Checkout the projects [homepage](https://guacamole.incubator.apache.org/) for more information.

## Prerequisites
You need a working **docker** installation and **docker compose** running on your machine.

## Quick start
Clone the GIT repository and start guacamole:

~~~bash
git clone "https://github.com/themxsz/guacamole-docker.git"
cd guacamole-docker-compose
./prepare.sh
docker compose up -d
~~~

Your guacamole server should now be available at `https://ip of your server:8443/`. The default username is `guacadmin` with password `guacadmin`.

## prepare.sh
`prepare.sh` is a small script that creates `./init/initdb.sql` by downloading the docker image `guacamole/guacamole` and start it like this:

~~~bash
docker run --rm 'guacamole/guacamole:x.x.x' /opt/guacamole/bin/initdb.sh --postgresql > ./init/initdb.sql
~~~

It creates the necessary database initialization file for postgres.

`prepare.sh` also creates the self-signed certificate `./nginx/ssl/self.cert` and the private key `./nginx/ssl/self-ssl.key` which are used
by nginx for https.

## reset.sh
To reset everything to the beginning, just run `./reset.sh`.

## WOL

Wake on LAN (WOL) does not work and I will not fix that because it is beyound the scope of this repo. But [zukkie777](https://github.com/zukkie777) who also filed [this issue](https://github.com/boschkundendienst/guacamole-docker-compose/issues/12) fixed it. You can read about it on the [Guacamole mailing list](http://apache-guacamole-general-user-mailing-list.2363388.n4.nabble.com/How-to-docker-composer-for-WOL-td9164.html)

**Disclaimer**

Downloading and executing scripts from the internet may harm your computer. Make sure to check the source of the scripts before executing them!
