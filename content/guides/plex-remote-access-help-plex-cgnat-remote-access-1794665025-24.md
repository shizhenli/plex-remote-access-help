---
title: "Plex Remote Access Behind CGNAT: Why Port Forwarding Fails and How to Confirm It"
description: "If your ISP uses CGNAT, your router cannot forward the Plex port. Learn how to confirm CGNAT, interpret WAN IP results, verify remote access, and recover safely."
seo_title: "Plex CGNAT Remote Access: Port Forwarding Blocked? Confirm and Fix"
seo_description: "If your ISP uses CGNAT, your router cannot forward the Plex port. Learn how to confirm CGNAT, interpret WAN IP results, verify remote access, and recover safely."
keywords:
  - "plex cgnat remote access"
date: 2026-11-22T12:06:17+08:00
publishDate: 2026-11-22T12:06:17+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are trying to enable Plex remote access, but your router cannot expose the Plex port because your ISP uses CGNAT.

## Confirm CGNAT on the router

Open your router's status page and find the WAN IP address. Compare it to the public IP shown by a browser-based IP lookup. If the WAN IP falls in 100.64.0.0/10 (for example, 100.64.x.x through 100.127.x.x), that is carrier-grade NAT. If the WAN IP differs from the public IP, CGNAT is also likely. Either result means port forwarding on your router cannot work.

## Check the Plex side

In Plex settings, open Remote Access and note the manually specified port. Then check your router's port forwarding list. If you cannot create a rule that maps that port to the Plex server's LAN IP, stop here: the router is not the problem. This is the point where **plex cgnat remote access** fails before any diagnosis can complete.

## Verification test

After any change, test from outside your home network using mobile data. Open the Plex app or the web player and attempt playback. A successful connection shows the server as reachable and media plays. If it still fails, CGNAT remains in effect.

## Recovery and rollback

If you added a port forwarding rule that cannot work, remove it to avoid confusion. Revert any manual port change in Plex back to automatic, then restart the Plex service. If you contacted your ISP for a public IP, confirm the change in writing before retesting.

If these checks confirm CGNAT and you need a working path,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) to review your setup.
