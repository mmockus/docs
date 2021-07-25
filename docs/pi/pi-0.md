---
sidebar_position: 1
---

# Pi-0

## Specifications
- Device: Rasberry Pi Zero W Rev 1.1
  - [Raspberry Pi Zero](https://smile.amazon.com/gp/product/B072N3X39J)
  - 16GB microSD
  - wired ethernet adapter
- Tools: [Balena Etcher](https://www.balena.io/etcher/)
- OS: [Raspberry Pi OS Lite](https://www.raspberrypi.org/software/operating-systems/)

Role(s): Pihole
Docker documentation on Pihole: 
- [https://pihole.github.io/](https://pihole.github.io/)
- [dockerhub](https://hub.docker.com/r/pihole/pihole/)

## Intent

I currently have PiHole running in my lab Proxmox as a VM. There are occasions when this server may go down or be rebooted. Since this is my DNS service, internet goes down when this happens. I wanted to have a physical redundant device.

## Reference

Techno-Tim has been a great asset to my learning

[PiHole on Docker and Kubernetes](https://techno-tim.github.io/posts/pihole-containerized/)

## Pihole Install

```shell
sudo apt update
sudo apt upgrade
```

### Install Docker
reference: <https://docs.docker.com/engine/install/ubuntu/>
Uninstall old versions
```shell
 sudo apt-get remove docker docker-engine docker.io containerd runc
 ```

Install via shell script
```shell
curl -sSL https://get.docker.com | sh
```

add current users permissions to run docker
```shell
sudo usermod -aG docker ${USER}
groups ${USER}
```
install python and pip
```shell
sudo apt-get install libffi-dev libssl-dev
sudo apt install python3-dev
sudo apt-get install -y python3 python3-pip
```
install docker compose
```shell
sudo pip3 install docker-compose
```

enable docker on startup
```shell
sudo systemctl enable docker
```

:::warning
Currently I could not get pihole to run in docker on a pi-zero.
:::

Docker run script
curl -sSL https://raw.githubusercontent.com/pi-hole/docker-pi-hole/master/docker_run.sh | sh
curl -sSL https://raw.githubusercontent.com/pi-hole/docker-pi-hole/master/docker_run.sh | cat

something like this should work but doesn't
```shell
curl -sSL https://raw.githubusercontent.com/pi-hole/docker-pi-hole/master/docker_run.sh | sed -e 's/127.0.0.1/{your-ip}/' | sh
```

curl -sSL https://raw.githubusercontent.com/pi-hole/docker-pi-hole/master/docker_run.sh > docker_run.sh

## Direct install 
```shell
curl -sSL https://install.pi-hole.net | bash
```

## Configure your Pihole

Now use the UI to configure your pihole. I restored my pihole from a backup of my primary pihole.

## Pihole Sync

Since this is a secondary pihole, I need to sync the DNS records.
<https://github.com/vmstan/gravity-sync/wiki/Installing#primary-pi-hole>
<https://github.com/vmstan/gravity-sync/wiki/System-Requirements>

### Create a pisync user

- Create a new user: `sudo adduser pisync`
- Grant user sudo: `usermod -aG sudo pisync`
- Verify: `id pisync`

### Install gravity-sync on your primary pihole

```shell
export GS_INSTALL=primary && curl -sSL https://gravity.vmstan.com | bash
```

### Install gravity-sync on your secondary pihole

Install
```shell
export GS_INSTALL=secondary && curl -sSL https://gravity.vmstan.com | bash
```

Check if gravity-sync is installed
```shell
./gravity-sync.sh compare
```

Automatically sync DNS records
```shell  
./gravity-sync.sh automate 
```
