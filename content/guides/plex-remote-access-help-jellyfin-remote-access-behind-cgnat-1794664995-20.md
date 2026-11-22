---
title: "Jellyfin Remote Access Behind CGNAT: When Port Forwarding Fails"
description: "Troubleshoot Jellyfin remote access when CGNAT blocks port forwarding. Learn to confirm CGNAT, test connectivity, and recover access."
seo_title: "Jellyfin Remote Access Behind CGNAT: Fix Port Forwarding"
seo_description: "Troubleshoot Jellyfin remote access when CGNAT blocks port forwarding. Learn to confirm CGNAT, test connectivity, and recover access."
keywords:
  - "jellyfin remote access behind cgnat"
date: 2026-11-22T10:06:00+08:00
publishDate: 2026-11-22T10:06:00+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are trying to set up Jellyfin remote access, but your router cannot expose the Jellyfin port because your ISP uses CGNAT.

## Confirm CGNAT Is the Cause

First, verify that CGNAT is actually blocking you. Log in to your router and find the WAN IP address. Compare it to the public IP address shown by a site like whatismyip.com. If the WAN IP is in a private range (10.x.x.x, 172.16.x.x, or 192.168.x.x) or differs from the public IP, CGNAT is likely active. Also, check your router's port forwarding page: if you cannot add a rule for the Jellyfin port (commonly 8096), or the rule has no effect, CGNAT is the culprit.

## Test External Reachability

With the port forward attempt in place, use an online port checker (e.g., canyouseeme.org) to test port 8096 from outside your network. If it reports "closed" or "filtered," CGNAT is blocking inbound connections. This confirms that **jellyfin remote access behind cgnat** requires a workaround, not just router configuration.

## Workarounds and Recovery

Since CGNAT prevents direct port forwarding, you need an alternative. Options include:
- Contact your ISP to request a public IP (often a paid add-on).
- Use a VPN with port forwarding (e.g., WireGuard with a VPS).
- Set up a reverse proxy tunnel (e.g., Cloudflare Tunnel or Tailscale).

If you attempt a workaround and it fails, roll back by disabling the new service and restarting your router to restore local access. Always keep a backup of your configuration.

## Verify Remote Access

After implementing a workaround, test from an external network: open a browser and go to your Jellyfin URL (e.g., https://yourdomain.com). If the login page loads, remote access is restored. If not, recheck the tunnel or VPN settings.

For personalized help with your setup,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
