---
title: "Jellyfin Remote Access Without Port Forwarding When CGNAT Blocks the Plex Port"
description: "When CGNAT blocks port forwarding for your Plex server, use this focused check to confirm the block and recover remote access without opening router ports."
seo_title: "Jellyfin Remote Access Without Port Forwarding: CGNAT Fix"
seo_description: "When CGNAT blocks port forwarding for your Plex server, use this focused check to confirm the block and recover remote access without opening router ports."
keywords:
  - "jellyfin remote access without port forwarding"
date: 2026-11-22T09:05:54+08:00
publishDate: 2026-11-22T09:05:54+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

## Troubleshooting

Your Plex server works at home, but outside access fails because the router cannot expose the Plex port due to ISP-level CGNAT. Start by confirming the block before changing anything. On the Plex host, open a terminal and run `curl -4 ifconfig.me`, then compare that public IP with the WAN address shown in your router status page. If the two addresses differ, or the router WAN address falls in 100.64.0.0/10, CGNAT is intercepting traffic and port forwarding cannot work. Next, check the Plex remote access page: if it stays red or shows indirect after a manual port test, stop editing router rules. For a practical workaround, enable a secure tunnel or relay that does not require inbound ports, then retest from a mobile network with Wi-Fi disabled. A successful result is the Plex app loading your library over cellular while the server dashboard shows a remote connection. If playback still fails, revert the tunnel setting and confirm local playback first, so you do not stack changes. For **jellyfin remote access without port forwarding**, the same logic applies: confirm CGNAT, avoid router port rules, and use an outbound tunnel or relay instead. Verification test: disconnect Wi-Fi on your phone, open Plex, play a two-minute clip, and confirm the dashboard reports remote playback. Rollback note: disable the tunnel or relay and restart the Plex service if remote access worsens. If the public and WAN addresses match but remote access still fails, the issue is not CGNAT and needs a separate diagnosis.

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) if you want a technician to review your address comparison and tunnel result.
