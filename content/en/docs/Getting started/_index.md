---
title: "Getting Started"
linkTitle: "Getting Started"
weight: 2
description: >
  How to get started?
---

## Get your device

You still need the Hardware? We are planning a small production run, but until that has happened, please refer to the production files and instructions located in our repositories.

* [OtterCastAudioV2](https://github.com/Ottercast/OtterCastAudioV2/tree/main/gerber_v2.1)
* [OtterCastAmp](https://github.com/Ottercast/OtterCastAudioAmp/tree/main/production_v1.2)

## Get the firmware

After acquiring your device, you may head to our [firmware section](/docs/firmware/#download-ready-made-images).

## Flashed, and now?

You can mount the SD-Card and change the initial configuration by edition the `config.ini` file, present on the first partition. You should add your Wifi credentials and give your Ottercast a lovely hostname, it will be displayed later when you are casting! If you need SSH access, you can add your public key by creating a `ssh_authorized_keys` file containing your key.

## It works!

Great, you did it! You may now [check out the supported protocols and start casting](/docs/supported-protocols/) or visit your Ottercasts web-interface by typing `<hostname>.local` into your browsers address bar.
