---
sidebar_position: 9
---

# Pi

## Hardware 

- [Raspberry Pi Zero](https://smile.amazon.com/gp/product/B072N3X39J)
- [Balena Etcher](https://www.balena.io/etcher/)
- [Raspberry Pi OS Lite](https://www.raspberrypi.org/software/operating-systems/)

## Setup

### create the SD

- Etch the image onto an appropriate microSD card.

### setup ssh and wifi

- Place an empty file called `ssh` (no file extension) in the root of the drive to enable SSH

- create `wpa_supplicant.conf`

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
country=US
update_config=1

network={
 ssid="<Name of your wireless LAN>"
 psk="<Password for your wireless LAN>"
}
```

:::note Future research
For some reason I could not get the Pi to start using an microHD-ethernet adapter. Future 
:::

### Install SD into Pi

- Install the SD card into the Pi
- Power on the Pi

## Initial Configuration

- Find the IP address of the PI on your network
- ssh in, default password in `raspberry`
```shell
ssh pi@192.168.1.17  
```

- Use the default configuration tool to set up your pi

```shell
sudo raspi-config
```

- 1 System Options
  - Password - change the password
  - Hostname - change to a hostname of your choice
- 6 Advanced Options
  - Expand the file system
- 8 Update  

```shell
sudo reboot
```

### By Shell

Config can also be executed by shell

:::note ToDo
Write up how to do this via shell 
:::


### Add user
Add an admin user other than `pi`

- Create a new user: `sudo adduser myuser`
- Grant user sudo: `usermod -aG sudo myuser`
- Verify: `id myuser`
- Log in as myuser and validate sudo: `sudo ls -l /etc/shadow`

## Network

Set Static IPs from the router

### disable wifi

```shell
rfkill block wlan
```