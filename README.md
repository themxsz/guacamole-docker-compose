# This fork is my personally used version of bosch's implementation without nginx, opting for Netbird's reverse proxy (configured seperately) instead.

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

**Disclaimer**

Downloading and executing scripts from the internet may harm your computer. Make sure to check the source of the scripts before executing them!
