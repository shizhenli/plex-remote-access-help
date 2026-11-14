---
title: "Plex Port Forwarding Not Working Because of CGNAT: Confirm and Recover"
description: "If your router cannot expose the Plex port because your ISP uses CGNAT, confirm the block and restore remote access with a focused, step-by-step check."
seo_title: "Plex Port Forwarding Not Working? Check CGNAT First"
seo_description: "If your router cannot expose the Plex port because your ISP uses CGNAT, confirm the block and restore remote access with a focused, step-by-step check."
keywords:
  - "plex port forwarding not working"
date: 2026-11-14T19:38:03+08:00
publishDate: 2026-11-14T19:38:03+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You set up a port forward for Plex, but remote access still fails, and you suspect your ISP is using CGNAT.

## Confirm the CGNAT block

Log in to your router and find its WAN or internet status page. Look for the assigned IP address. Compare it with the public IP shown by a browser-based IP checker. If the router's WAN address is in a private range (10.x.x.x, 172.16.x.x–172.31.x.x, or 192.168.x.x) or differs from the public IP, CGNAT is likely blocking the forward. A result where the router WAN IP equals the public IP means CGNAT is not the cause, and you should recheck the port-forward rule itself.

## Interpret the result correctly

If the addresses differ, your router cannot expose the Plex port to the internet no matter how the rule is written. This is the cgnat blocks port forwarding condition, and it explains why **plex port forwarding not working** persists after router changes. Do not keep editing the rule; the block happens upstream.

## Verification test

From a device on mobile data (not your home Wi-Fi), open canyouseeme.org and test the exact Plex external port. A timeout or refused connection confirms the port is not reachable. If the test succeeds, the forward is working and the issue is elsewhere.

## Recovery and next steps

If CGNAT is confirmed, contact your ISP and request a public or static IP, or ask whether they offer one. Until then, disable the manual port forward to avoid false expectations and use Plex Relay as a temporary fallback. If you need a guided diagnosis before changing ISP settings,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
