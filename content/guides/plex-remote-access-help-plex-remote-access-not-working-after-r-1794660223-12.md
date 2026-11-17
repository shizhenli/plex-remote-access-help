---
title: "Plex Remote Access Not Working After Router Change: Green Status but Playback Fails"
description: "After a router change, Plex shows remote access as green but remote playback fails. Follow these focused checks to confirm port forwarding and firewall rules, then verify and recover."
seo_title: "Plex Remote Access Not Working After Router Change: Green Status but Playback Fails"
seo_description: "After a router change, Plex shows remote access as green but remote playback fails. Follow these focused checks to confirm port forwarding and firewall rules, then verify and recover."
keywords:
  - "plex remote access not working after router change"
date: 2026-11-17T11:05:44+08:00
publishDate: 2026-11-17T11:05:44+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You replaced your router, and now Plex Remote Access shows green, but remote clients still cannot play anything. This guide focuses on that exact symptom: the status looks fine, yet playback fails.

## Confirm the router's port forwarding rule
Log into the new router and find its port forwarding section. The rule must forward the external port you chose in Plex (often 32400) to the Plex server's current LAN IP on the same port, using TCP. If the rule is missing or points to an old IP, recreate it. Result interpretation: if the rule exists and matches the server's current IP, move on; if not, fix it and retest.

## Check the server's LAN IP and firewall
On the Plex server, confirm its LAN IP has not changed since the router swap. If it is dynamic, set a DHCP reservation on the new router so the IP stays fixed. Then check the server's firewall: allow inbound TCP on the Plex port for private networks. Result interpretation: a changed IP or a blocked port explains why the green status is misleading.

## Verify from outside your network
Use a phone on cellular data (Wi-Fi off) and open the Plex app. Try to play a small file. Success means the remote client starts playback within a few seconds. Failure means the forwarded port is still not reachable; recheck the rule and firewall.

## Rollback note
If you changed multiple router settings, restore the previous working configuration or reboot the router and server, then reapply only the port forward and firewall allowance.

If **plex remote access not working after router change** persists after these checks, the new router may be blocking the port or your ISP may use CGNAT.

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) with your router model and Plex port settings.
