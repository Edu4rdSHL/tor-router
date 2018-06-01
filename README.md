# TOR Router

Tor Router allow you to use TOR as a transparent proxy and send all your trafic under TOR, the only that you need is:

# Installing

~$ git clone https://github.com/Edu4rdSHL/tor-router && cd ./tor-router && sudo bash install.sh

# Uninstalling/Stoping

Move your /etc/tor/torrc.backup file to /etc/tor/torrc, disable the tor-router.service using systemctl, remove /usr/bin/tor-router and /etc/systemd/system/tor-router.service and restart your computer.
