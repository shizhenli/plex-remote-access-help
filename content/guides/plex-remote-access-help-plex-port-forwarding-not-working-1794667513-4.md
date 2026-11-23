---
title: "Plex Port Forwarding Not Working When CGNAT Blocks the Router"
description: "Plex port forwarding not working because your ISP uses CGNAT? Learn how to confirm CGNAT, test your public IP, and recover remote access without a public port."
seo_title: "Plex Port Forwarding Not Working: CGNAT Blocks Router Fix"
seo_description: "Plex port forwarding not working because your ISP uses CGNAT? Learn how to confirm CGNAT, test your public IP, and recover remote access without a public port."
keywords:
  - "plex port forwarding not working"
date: 2026-11-23T11:06:00+08:00
publishDate: 2026-11-23T11:06:00+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You set up a port forward for Plex, but remote access still fails because your ISP places you behind CGNAT, so the router cannot expose the Plex port.

## Confirm the CGNAT block

First, compare the WAN address shown in your router's status page with the public IP that Plex and external sites report. If the router WAN address falls in 100.64.0.0/10, or it differs from the public IP, CGNAT is blocking the forward. A matching public IP means the problem is elsewhere, so stop here and recheck the forward rule.

Next, verify the Plex port itself. In Plex settings, note the manually specified public port, then use an external port checker against your public IP. A closed result while the router rule exists confirms the ISP is not passing the port through.

## Test from outside

Disable Wi-Fi on a phone and open your Plex server through the Plex app. If it fails while the same server works on home Wi-Fi, the remote path is still blocked. This is the expected result when CGNAT is in play, and it explains why **plex port forwarding not working** persists even after you recreate the rule.

## Recover without a public port

Ask your ISP for a public or static IP; if they refuse, switch to a VPN or tunnel that provides a public relay, or use Plex Relay as a temporary fallback. Keep a copy of your original router rule so you can restore it if the ISP later assigns a public address. If you need a guided diagnosis,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
