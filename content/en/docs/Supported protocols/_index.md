---
title: "Supported protocols"
linkTitle: "Supported protocols"
weight: 3
description: >
  Which audio streaming services/protocols are supported?
---

Ottercast is open source! If your favorite app/protocol is missing, open an [Issue](https://github.com/Ottercast/buildroot-ottercast-audio/issues) or integrate it yourself and send a [Pull Request](https://github.com/Ottercast/buildroot-ottercast-audio/pulls).

## Snapcast
[Snapcast](https://github.com/badaix/snapcast) is a multiroom-capable network audio player.  
Ottercast can act as a Snapcast client and will connect to a Snapcast server which is streaming audio.  
Multiple Ottercasts (and other Snapcast clients) can connect to the same server and will play perfectly synced audio.

Ottercast can also work as a Snapcast server and stream audio from it's Line-In port to multiple Snapcast clients.

## Spotifyd / Spotify Connect

<div class="row">
<div class="col-md-7">

[Spotifyd](https://github.com/Spotifyd/spotifyd) is a Spotify Connect client, written in Rust, utilizing the librespot library.  
**Requires Spotify Premium.**

</div>
<div class="col-md-4">
<img src="/assets/images/spotify.png" alt="Screenshot of Spotifyd" class="img-responsive">
</div>

</div>

## Shairport Sync / AirPlay


<div class="row">
<div class="col-md-7">

[Shairport Sync](https://github.com/mikebrady/shairport-sync) is an open source reimplementation of the AirPlay protocol.  
You can select your Ottercast as an AirPlay target on your iOS/macOS devices.  
Shairport supports full audio synchronisation, which means audio/video sync will be enforced.

</div>
<div class="col-md-4">
<img src="/assets/images/airplay.png" alt="Screenshot of Airplay" class="img-responsive">
</div>

</div>

## PulseAudio Sink

<div class="row">
<div class="col-md-6">

Ottercast can act as a PulseAudio Sink via `module-native-protocol-tcp`.  
Use `paprefs` to enable local discovery and ensure `avahi-daemon` is running.  

</div>
<div class="col-md-5">
<img src="/assets/images/paprefs.png" alt="Screenshot of paprefs" class="img-responsive">
</div>
</div>

## Line In

Not really a protocol, but a supported input method! Connect a line-in via the TRS jack on the back of the OtterCastAmp or the left TRS jack of the OtterCastAudio. Activate the input through the web interface and enjoy your device as an amplifier or wireless audio capture card!

You may need to adjust the input volume by running `PULSE_SERVER=x.x.x.x pavucontrol` and e.g. lowering the input volume to 30%.
