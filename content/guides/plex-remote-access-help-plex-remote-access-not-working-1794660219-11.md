---
title: "Plex Remote Access Green but Playback Fails: Fix the Relay vs. Direct Connection Mismatch"
description: "Plex shows remote access is available but playback fails on remote clients. Fix the relay vs. direct connection mismatch with focused checks and a verification test."
seo_title: "Plex Remote Access Not Working: Green Status but Playback Fails"
seo_description: "Plex shows remote access is available but playback fails on remote clients. Fix the relay vs. direct connection mismatch with focused checks and a verification test."
keywords:
  - "plex remote access not working"
date: 2026-11-17T10:05:44+08:00
publishDate: 2026-11-17T10:05:44+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You see green under Remote Access in Plex settings, but when you try to play something from outside your home network, the client spins or errors out.

## Confirm whether the remote client is using a relay or direct connection

On the remote device, open the Plex client's playback info or dashboard. If the connection shows as indirect or relay, Plex is falling back to a limited relay even though the server reports green. That mismatch is the failure: the status page checks reachability, not whether the client can establish a direct stream.

## Check the server's published port and manual port setting

In Plex server settings, go to Remote Access. Note whether it says Fully accessible or shows a relay indicator. If you have manually specified a public port, confirm that port is forwarded on your router to the server's LAN IP and that the server's firewall allows it. If the status is green but the client is relayed, disable and re-enable Remote Access, then re-check the client's connection type. A green status with a relayed client means the direct path is blocked.

## Verification test

From the remote client, play a short low-bitrate clip. In the Plex dashboard, confirm the stream shows direct or secure direct, not relay. If it still relays, the direct connection is not working and **plex remote access not working** is the actual condition despite the green indicator.

## Rollback and recovery

If changes make things worse, revert the manual port and any firewall rule to their previous values, then restart the Plex server service. Re-enable Remote Access and confirm the original green status returns before retesting.

If the client remains relayed after these checks,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) with your dashboard connection details.
