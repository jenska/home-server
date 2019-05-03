# docker home server
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

Don't forget to 
```bash
  apt update
  apt upgrade
```

#### Docker
```bash
  apt install apt-transport-https ca-certificates curl software-properties-common
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg 
  apt-key add -
  
```
