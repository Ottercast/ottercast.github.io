---
title: "Firmware"
linkTitle: "Firmware"
weight: 3
description: >
  Details about the Firmware, Software, Webinterface
---

Ottercast Firmware is built using [buildroot](https://buildroot.org/).  
It's running a mainline Linux kernel, with GNU userland, systemd, PulseAudio and Avahi.

## Download ready-made images

Current firmware binaries can be found on GitHub at:  
[Ottercast/buildroot-ottercast-audio](https://github.com/Ottercast/buildroot-ottercast-audio/releases)  

Firmware images are automatically built for each commit via GitHub Actions. 

## Flashing the image

The procedure is identical to a Raspberry Pi. Make sure to unzip (.gz/gzip) the firmware before writing it to a card.   
Firmware binaries are disk images, containing partitions and can be written directly to an SD card or eMMC flash.  

*Do NOT copy the file onto a SD card as a file.*   
It needs to be written as a disk image using a tool like [Etcher](https://www.balena.io/etcher/), [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/) or [dd](https://wiki.archlinux.org/index.php/Dd).

## Initial configuration

After flashing, you can mount the FAT32 partition and edit the `config.sh` and (optional) `ssh_authorized_keys`.  
Configure your WiFi credentials, SSH public keys and a name for the device. 

## Building your own image

Building your own image can be done on a regular x86_64 machine running Linux. 

Make sure to fulfill the [buildroot dependencies](https://buildroot.org/downloads/manual/manual.html#requirement):  

Distribution | Command
--- | --- 
Arch/Manjaro | `pacman -S base-devel git wget perl unzip rsync ncurses`
Debian/Ubuntu/Mint | `apt install build-essential git wget unzip rsync libncurses-dev`

_These dependency lists are untested, please report if something is missing!_

```
mkdir ottercast
cd ottercast
git clone https://github.com/Ottercast/buildroot-ottercast-audio.git
wget https://buildroot.org/downloads/buildroot-2020.11.3.tar.gz
tar xfv buildroot-2020.11.3.tar.gz
cd buildroot-2020.11.3/
make BR2_EXTERNAL=../buildroot-ottercast-audio/buildroot/ ottercast_audio_v2_defconfig
```

This will generate a config file in the buildroot folder.  
  
(optional) Use `make menuconfig` to change buildroot settings (enable/disable packages, compile settings, etc.).  
(optional) Use `make linux-menuconfig` to change kernel parameters.  
  
Compile the firmware using `make -j$(nproc)`.   
This will take ~60min on a very fast machine with stable internet connection.  
First compilation will download, compile and assemble a full Linux installation from scratch.  
__This can take up to several hours. Be patient! Changes will build much faster.__ 
  
The resulting disk image will be located at `buildroot-(version)/output/images/sdcard.img`.  

The external tree can be found at: [https://github.com/Ottercast/buildroot-ottercast-audio](Ottercast/buildroot-ottercast-audio).

## Webinterface

The webinterface is written in PHP and running as a CGI script.  
uhttpd is used as a webserver and serves `/var/www` on Port 80 via HTTP.  
Frontend is using Bootstrap and jQuery.