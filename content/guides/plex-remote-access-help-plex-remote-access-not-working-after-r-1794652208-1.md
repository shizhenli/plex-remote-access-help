---
title: "Plex Remote Access Not Working After Router Change: Fix Green Light but No Playback"
description: "After a router change, Plex remote access shows green but playback fails. Follow these focused checks to restore remote streaming without starting over."
seo_title: "Plex Remote Access Not Working After Router Change: Green Light, No Playback Fix"
seo_description: "After a router change, Plex remote access shows green but playback fails. Follow these focused checks to restore remote streaming without starting over."
keywords:
  - "plex remote access not working after router change"
date: 2026-11-14T19:38:03+08:00
publishDate: 2026-11-14T19:38:03+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You changed your router, Plex now shows remote access as available, but remote clients still cannot play anything—this is a classic sign that the green status is only half the story. The fix is to verify the actual data path, not just the indicator.

## Confirm the server's current LAN address

On the Plex server, open Settings > Network and note the LAN IP. Then check your new router's DHCP client list. If the server's IP changed, any manual port forward you recreated may point to the old address. Update the forward to the current IP, or set a DHCP reservation so it stops moving. Result to expect: the router's forward and Plex's LAN IP match exactly.

## Verify the external port actually reaches Plex

In Plex remote access settings, confirm the manually specified public port. On the router, ensure the forward uses TCP and the same port. From a device outside your network, test that port with an online port checker. If it reports closed, the forward is wrong or the router's firewall is blocking it. If it reports open, move on.

## Rule out the new router's security features

Many routers enable SPI firewall, DoS protection, or "secure" NAT by default. Temporarily disable those for the server's forward, then retest. Also confirm the server's OS firewall still allows Plex on the forwarded port. This is often where **plex remote access not working after router change** hides—the green light reflects Plex's cloud check, not real playback.

## Verification test

From cellular data (not home Wi-Fi), play a short clip in the Plex app. Success means playback starts within a few seconds. If it still fails, note whether the client shows "indirect" or "relay"—that points to a port issue, not account access.

## Rollback note

If changes make local access worse, revert the router forward and firewall edits to their previous values, then restart the Plex service. For guided diagnosis,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
