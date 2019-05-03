# Docker Home Server
a personal, docker-based home server project

## Objectives 
Build a multi-purpose, linux-based home server based on legacy hardware for
- Media streaminng
- Network storage
- Network administration
- Programming tools

## Basics 
Several Raspberry PIs and a NAS were already in place at my household. I wasn't satisfied with the performance and the maintenance effort of this devices and decided to build an all-in-one-machine for all my use-cases in mind.

### Hardware Recommendation
- 2-4 core amd64 CPU
- at least 4 GB RAM
- mainboard with SATA and fast LAN adapter 
- SSD for OS and docker images
- tons of NAS HDDs

### Core Software Installation
#### Ubuntu Server 18.04 LTS
Download and install as described at <https://www.ubuntu.com/download/server>. OpenSSH packages are included by default.

If you want to run your own DNS server (as a pi-hole docker container), please follow these steps:

Login as root or enter ```sudo -i```
Check if systemd-resolved is listening to port 53
```bash
  netstat -nlpt | grep 53
```
If yes, then stop and disable this service
```bash
 systemctl stop systemd-resolved
 systemctl disable systemd-resolved.service
 systemctl stop systemd-resolved
```
Do not forget to add your host name <your-host> to the hostname to /etc/hosts
```bash
  nano /etc/hosts
```
Add your host name to the first and second line of this file
```
127.0.0.1       localhost.localdomain   localhost <your-host>
::1             localhost6.localdomain6 localhost6 <your-host>6

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
Save with ^X and 'Y'

#### Docker
Setup script follows soon...

Login as root or enter ```sudo -i``` 

```bash
  apt install apt-transport-https ca-certificates curl software-properties-common
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
  add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
  apt update
  apt install docker_ce
```

#### Docker Composer or Portainer
