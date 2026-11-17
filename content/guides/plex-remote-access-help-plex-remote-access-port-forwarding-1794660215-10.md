---
title: "CGNAT Blocks Port Forwarding: Confirm the ISP Limit and Recover Plex Remote Access"
description: "Your router cannot expose the Plex port because the ISP uses CGNAT. Confirm the block, test the result, and recover remote access without guessing."
seo_title: "CGNAT Blocks Plex Port Forwarding: Confirm and Recover"
seo_description: "Your router cannot expose the Plex port because the ISP uses CGNAT. Confirm the block, test the result, and recover remote access without guessing."
keywords:
  - "plex remote access port forwarding"
date: 2026-11-17T09:18:00+08:00
publishDate: 2026-11-17T09:18:00+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are trying to set up **plex remote access port forwarding**, but your router cannot expose the Plex port because the ISP uses CGNAT.

## Confirm the CGNAT block

Open your router's status page and note the WAN IPv4 address. Then visit a public IP-checking site from the same network and note the public IPv4 address. If the router WAN address falls in 100.64.0.0/10, or it differs from the public address, CGNAT is in front of your router. In that case, no port-forward rule on your router can expose the Plex port to the internet. If the two addresses match, CGNAT is not the blocker and you should revisit the forward rule itself.

## Verify the port is unreachable

With Plex running, use an external port checker against your public IP and the Plex port. A closed or filtered result confirms the port is not reachable from outside. A successful open result means the forward is working and the issue lies elsewhere. Do not change Plex settings until this test is complete.

## Recover remote access

Ask your ISP for a public or static IPv4 address, or whether CGNAT can be removed on your plan. If that is not available, use a relay or tunnel service that does not require inbound port forwarding, and point Plex remote access through it. Keep a note of your original router WAN and forward settings so you can restore them if the ISP change is reversed. After any change, rerun the external port check before trusting the Plex status indicator.

If the external check still fails after these steps,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) with your WAN address, public address, and port-check result.
