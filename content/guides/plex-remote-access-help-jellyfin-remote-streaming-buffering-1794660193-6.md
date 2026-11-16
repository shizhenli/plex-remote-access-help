---
title: "Jellyfin Remote Streaming Buffering: Fix Relay Playback Stalls"
description: "Remote Jellyfin playback buffers through relay. Follow these checks to diagnose relay buffering and restore smooth streaming."
seo_title: "Jellyfin Remote Streaming Buffering — Fix Relay Playback"
seo_description: "Remote Jellyfin playback buffers through relay. Follow these checks to diagnose relay buffering and restore smooth streaming."
keywords:
  - "jellyfin remote streaming buffering"
date: 2026-11-16T11:05:44+08:00
publishDate: 2026-11-16T11:05:44+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You're outside your home network, and Jellyfin playback keeps buffering because it's routing through a relay instead of a direct connection.

## Confirm the relay route
Open the Jellyfin dashboard while streaming remotely. In the active sessions panel, check the connection type. If it shows "Relay" or a relay icon, your server isn't reachable directly. This confirms the symptom: **jellyfin remote streaming buffering** through relay.

## Check direct connectivity
From the remote device, open a browser and try reaching your server's public address and port (for example, https://yourdomain:8920). If it times out, the port isn't forwarded or is blocked. On your router, verify the port forward rule points to the Jellyfin server's current LAN IP. If the IP changed, update the rule. Also confirm your ISP isn't using CGNAT: compare the router's WAN IP with the public IP shown on a what-is-my-ip site. If they differ, direct connections won't work without a tunnel.

## Test with a small file
Play a short 720p clip remotely. If it plays without buffering, the relay is handling small files but choking on larger ones. If it still buffers, note the exact error or spinner duration. A relay that buffers on every file suggests bandwidth limits or server upload saturation.

## Adjust and verify
In Jellyfin's networking settings, ensure "Enable remote connections" is on and the public HTTPS port matches your forward. Restart the server. Then repeat the remote playback test and check the session panel again. A direct connection or stable relay playback means the fix held.

## Rollback note
If changes break local access, revert the port forward and networking settings to their previous values, then restart Jellyfin. For guided diagnosis,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
