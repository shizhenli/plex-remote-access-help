---
title: "Plex CGNAT Remote Access: When Port Forwarding Is Blocked"
description: "Is CGNAT blocking your Plex remote access? Learn how to confirm the block, test alternatives, and recover your setup without port forwarding."
seo_title: "Plex CGNAT Remote Access: Fix Port Forwarding Blocked"
seo_description: "Is CGNAT blocking your Plex remote access? Learn how to confirm the block, test alternatives, and recover your setup without port forwarding."
keywords:
  - "plex cgnat remote access"
date: 2026-11-17T08:10:42+08:00
publishDate: 2026-11-17T08:10:42+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You're setting up Plex remote access, but your router can't expose the Plex port because your ISP uses CGNAT, and you're stuck before completing a controlled diagnosis.

## Confirm the CGNAT Block
First, verify that CGNAT is the actual cause. Log in to your router and find its WAN IP address. Then visit a site like whatismyip.com to see your public IP. If the router's WAN IP is in a private range (10.x.x.x, 172.16.x.x–172.31.x.x, or 192.168.x.x) or differs from the public IP, CGNAT is likely blocking port forwarding. Also check your ISP account page or call support to confirm you're behind CGNAT.

## Interpret the Result
If the WAN IP is private or mismatched, your router cannot forward ports to the internet. This is the expected outcome: **plex cgnat remote access** fails because the ISP shares one public IP among many customers. Do not waste time on port forwarding rules—they won't work.

## Verification Test
After confirming CGNAT, test whether remote access works at all. Disable remote access in Plex, then re-enable it. If Plex still shows "Not available outside your network" and the port check fails, CGNAT is confirmed. Alternatively, use an online port checker against your public IP and Plex port; a closed result confirms the block.

## Workarounds and Recovery
Since port forwarding is impossible, use Plex Relay (enabled by default in Settings > Network) for remote access, though it's limited to 1 Mbps for free users. For full speed, consider a VPN with port forwarding or a reverse proxy tunnel. If you change ISP settings or move to a different network, re-run the checks above. To roll back, simply disable any workaround and return to direct connection once CGNAT is removed.

If you need personalized guidance,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
