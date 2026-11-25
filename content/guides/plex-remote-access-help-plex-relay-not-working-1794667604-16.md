---
title: "Plex Relay Buffering on Remote Playback: A Step-by-Step Fix"
description: "Troubleshoot Plex relay buffering during remote playback. Check relay status, bandwidth limits, and server load to restore smooth streaming."
seo_title: "Plex Relay Not Working: Stop Remote Playback Buffering"
seo_description: "Troubleshoot Plex relay buffering during remote playback. Check relay status, bandwidth limits, and server load to restore smooth streaming."
keywords:
  - "plex relay not working"
date: 2026-11-25T10:05:49+08:00
publishDate: 2026-11-25T10:05:49+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You're trying to watch your Plex library remotely, but playback keeps buffering because it's routing through Plex Relay instead of a direct connection.

## Check Relay Status and Bandwidth

Open Plex Web, go to Settings > Remote Access, and confirm whether "Relay" is enabled. If it's on, Plex falls back to relay when direct access fails. Next, check the relay bandwidth limit under Settings > Network > "Relay bandwidth limit." The default is 1 Mbps, which is too low for most video. Set it to 3 Mbps or higher, then save. If the value is already high, move on.

## Verify Server Upload Speed

Run a speed test on the server machine. Relay traffic passes through Plex's servers, so your upload speed caps playback. If upload is below 5 Mbps, lower the remote stream quality in the client app (e.g., 2 Mbps 720p) to reduce buffering.

## Check Server CPU and Transcoding

During remote playback, open Plex Dashboard and look at the Now Playing section. If the stream shows "Transcode," the server may be overloaded. Stop other streams or disable transcoding by setting the client to "Direct Play" if the file format allows. High CPU usage during relay playback often causes repeated buffering.

## Verification Test

After making changes, play a remote video for two minutes. If buffering stops, relay is working within limits. If it persists, disable relay entirely (Settings > Network > uncheck "Enable Relay") and test direct remote access. If direct access also buffers, the issue is your upload speed or network, not relay.

## Rollback Note

If disabling relay breaks remote access completely, re-enable it and revert bandwidth to the previous value. Keep a note of original settings before changes.

If these steps don't resolve your **plex relay not working** issue,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) for a guided diagnosis.
