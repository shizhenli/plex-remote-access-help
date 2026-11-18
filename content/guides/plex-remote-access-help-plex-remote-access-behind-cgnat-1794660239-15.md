---
title: "Plex Remote Access Behind CGNAT: When Port Forwarding Is Blocked"
description: "Stuck at the CGNAT blocks port forwarding step? Learn how to confirm CGNAT, test your public IP, and recover Plex remote access when your ISP won't expose the port."
seo_title: "Plex Remote Access Behind CGNAT: Fix Port Forwarding Blocked"
seo_description: "Stuck at the CGNAT blocks port forwarding step? Learn how to confirm CGNAT, test your public IP, and recover Plex remote access when your ISP won't expose the port."
keywords:
  - "plex remote access behind cgnat"
date: 2026-11-18T09:05:52+08:00
publishDate: 2026-11-18T09:05:52+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You're trying to set up Plex remote access, but your router can't forward the Plex port because your ISP uses CGNAT, and you're stuck before completing a controlled diagnosis.

## Confirm CGNAT Is the Cause

First, compare your router's WAN IP with the public IP Plex sees. On your router's status page, note the WAN address. Then, from a device on the same network, visit a site that shows your public IP. If the WAN IP is in a private range (10.x.x.x, 172.16.x.x–172.31.x.x, or 192.168.x.x) or differs from the public IP, CGNAT is likely active. A result showing a private WAN IP is a strong indicator that **plex remote access behind cgnat** will block port forwarding.

## Check the Plex Port Forwarding Step

In Plex, go to Settings > Remote Access and note the manually specified public port. Then open your router's port forwarding page and try to create a rule for that port to your server's LAN IP. If the router refuses, warns about a double NAT, or the rule has no effect, stop here—CGNAT is preventing the port from being exposed.

## Verification Test

After any change, use an external port checker (from outside your network) to test the Plex port. A closed or filtered result confirms the port is not reachable. Also, toggle Remote Access off and on in Plex; if it stays red or quickly fails, CGNAT is still blocking.

## Recovery and Next Steps

If you confirmed CGNAT, roll back any half-created port forwarding rules to avoid conflicts. Contact your ISP and ask for a public IPv4 address or to disable CGNAT; if unavailable, consider a VPN with port forwarding or a relay service. For guided help with your specific setup,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
