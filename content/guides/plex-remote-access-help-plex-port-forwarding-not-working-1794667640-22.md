---
title: "CGNAT Blocks Plex Port Forwarding: Confirm the Block and Recover"
description: "Plex port forwarding not working because CGNAT blocks the port? Confirm the block, test your WAN IP, and recover remote access with practical steps."
seo_title: "Plex Port Forwarding Not Working: CGNAT Block Diagnosis and Fix"
seo_description: "Plex port forwarding not working because CGNAT blocks the port? Confirm the block, test your WAN IP, and recover remote access with practical steps."
keywords:
  - "plex port forwarding not working"
date: 2026-11-26T09:05:00+08:00
publishDate: 2026-11-26T09:05:00+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You set up a port forward for Plex, but remote access still fails because your ISP uses CGNAT.

## Confirm the CGNAT block

On the Plex server, open a terminal and run `curl ifconfig.me`. Write down the public IP it returns. Next, log in to your router and find its WAN or internet IP address. Compare the two addresses.

If the router WAN address is in a private range such as 10.x.x.x, 100.64.x.x through 100.127.x.x, or 192.168.x.x, while the curl result is a different public address, your ISP is using CGNAT. That means the router cannot expose the Plex port to the internet, so **plex port forwarding not working** is expected. If both addresses match, CGNAT is not the cause and you should recheck the port forward rule.

## Verification test

From a device outside your home network, such as a phone on cellular data, open a browser and visit `https://www.yougetsignal.com/tools/open-ports/`. Enter your public IP and the Plex port. A closed result confirms the port is not reachable. You can also try `telnet <public-ip> <port>` from an external machine; a timeout or refusal means the port is blocked.

## Recovery options

Ask your ISP for a public or static IP address, which removes the CGNAT layer. If that is unavailable, use a relay or tunnel service that does not require inbound port forwarding. Keep a note of your original router settings so you can restore them if you change ISPs or plans.

If you need a guided review of your setup,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
