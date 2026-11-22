---
title: "Jellyfin Remote Streaming Buffering Through Relay: Diagnose and Fix"
description: "Stop Jellyfin remote streaming buffering when playback routes through relay. Follow these focused checks to confirm the cause and restore smooth playback."
seo_title: "Jellyfin Remote Streaming Buffering via Relay: Fix It"
seo_description: "Stop Jellyfin remote streaming buffering when playback routes through relay. Follow these focused checks to confirm the cause and restore smooth playback."
keywords:
  - "jellyfin remote streaming buffering"
date: 2026-11-22T11:06:05+08:00
publishDate: 2026-11-22T11:06:05+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You're outside your home network, Jellyfin starts playing through relay, and the stream buffers every few seconds.

## Confirm relay is actually the path
Open the Jellyfin dashboard while the remote stream is active. Under Active Devices, check the connection type for that session. If it shows relay or a remote address that is not your public IP, the stream is being proxied. Note the reported bitrate; relay often caps it well below your media's bitrate, which causes repeated buffering.

## Check the relay bandwidth cap
In Jellyfin, go to Settings > Networking and find the relay or remote streaming bandwidth limit. Compare it to the bitrate of the file being played. If the cap is lower, the server throttles the stream and the client rebuffers. Raise the cap only if your upload can sustain it; otherwise transcode the file to a lower bitrate before playing.

## Test direct remote access
Temporarily disable relay in the same networking settings, then retry playback from the remote device. If the stream connects directly and stops buffering, relay was the bottleneck. If it fails to connect, your port forwarding or remote access configuration needs attention before relay can be bypassed.

## Verification
Play a two-minute clip remotely with relay enabled and watch the dashboard. A stable session should show a steady bitrate near the file's rate and no repeated buffering events. If buffering persists, re-enable relay and lower the client's quality setting as a stopgap.

## Rollback
If changes make remote access worse, restore the previous relay and bandwidth settings, then confirm local playback still works. For **jellyfin remote streaming buffering** that survives these checks,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) with your dashboard session details.
