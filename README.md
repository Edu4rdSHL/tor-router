# TOR Router

Tor Router allow you to use TOR as a transparent proxy and send all your trafic under TOR **INCLUDING DNS REQUESTS**, the only that you need is: a system using systemd (if you want to use the service) and tor.

TOR router doesn't touch system files as the rest of tools for routing  your taffic does and the reason  is: there isn't needed to move files for routing traffic, also moving files is a bad idea since that a fail in the script/tool can break your system connection without you knowing what has happened.

# Script to install on distros using SystemD only

If you are using BlackArch Linux (https://blackarch.org) you can install the script from the repos using the following command: `# pacman -S tor-router`

To install from source:

**Note that you need BASH, not sh**

```
~$ git clone https://gitub.com/edu4rdshl/tor-router.git && cd ./tor-router && sudo bash install.sh
```

# Usage

In distros using systemd, you should consideer using the install.sh script, anyways the process to install/configure tor-router is described here.

**It script require root privileges**

1. Open a terminal and clone the script using the following command:
```
~$ git clone https://gitub.com/edu4rdshl/tor-router.git && cd tor-router/files
```
2. Put the following lines at the end of /etc/tor/torrc
```
# Seting up TOR transparent proxy for tor-router
VirtualAddrNetwork 10.192.0.0/10
AutomapHostsOnResolve 1
TransPort 9040
DNSPort 5353
```
3. Restart the tor service
4. Execute the tor-router script as root
```
# sudo ./tor-router
```
5. Now all your traffic is under TOR, you can check that in the following pages: https://check.torproject.org and for DNS tests: https://dnsleaktest.com 
6. In order to automate the process of the script, you should add it to the SYSTEM autostart scripts according that the init that you are using, for systemd we have a .service file in the *files* folder.

# Uninstalling/Stoping

Delete the tor-router configuration lines in /etc/tor/torrc, disable the tor-router.service using systemctl (if you used the install.sh script), remove /usr/bin/tor-router, /etc/systemd/system/tor-router.service and restart your computer.

# Proof of concept

After of run the script, follow the next steps to ensure that all is working as expected:

- **Ip hidden and TOR network configured**: Visit https://check.torproject.org, you should see a message like it:

![Alt text](https://i.imgur.com/FboGoCr.png "Ip check")

- **Checking DNS Leaks**: Visit https://dnsleaktest.com and make a extended test to see what are your DNS. You shloud get some like it:

![Alt text](https://i.imgur.com/IEdfVHj.png "DNS check")

# Distros using the script

BlackArch Linux: https://github.com/BlackArch/blackarch/blob/master/packages/tor-router
