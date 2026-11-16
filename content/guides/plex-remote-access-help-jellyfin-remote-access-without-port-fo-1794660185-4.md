---
title: "Jellyfin Remote Access Without Port Forwarding: When CGNAT Blocks the Plex Port"
description: "Plex remote access fails because CGNAT blocks port forwarding. Learn how to confirm CGNAT, test alternatives, and recover safely without exposing your server."
seo_title: "Jellyfin Remote Access Without Port Forwarding: CGNAT Fix"
seo_description: "Plex remote access fails because CGNAT blocks port forwarding. Learn how to confirm CGNAT, test alternatives, and recover safely without exposing your server."
keywords:
  - "jellyfin remote access without port forwarding"
date: 2026-11-16T09:05:41+08:00
publishDate: 2026-11-16T09:05:41+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are trying to reach your Plex server from outside your home network, but the router cannot expose the Plex port because your ISP uses CGNAT.

## Confirm CGNAT Is the Blocker

Open your router's WAN status page and note the WAN IPv4 address. Then visit a public IP-check page from a device on the same network and note the public address. If the router WAN address falls in 100.64.0.0/10 (for example, 100.64.x.x through 100.127.x.x), or it differs from the public address, CGNAT is confirmed. Result interpretation: a private or shared WAN address means no port-forward rule can ever be reached from the internet.

## Test Whether the Port Is Reachable

From a phone on cellular data (Wi-Fi off), open a port-checking site and test the Plex port you configured. A closed or filtered result confirms the ISP boundary, not a router misconfiguration. Do not keep changing router rules; they cannot override CGNAT.

## Use a Relay or Tunnel Instead

For remote viewing without inbound ports, enable Plex Relay in Settings > Network and set a manual port only if your ISP provides a public address. Alternatively, use a VPN tunnel such as Tailscale on the server and client, which avoids inbound forwarding entirely. This is the practical path for **jellyfin remote access without port forwarding** when the ISP controls the address.

## Verify and Roll Back

After enabling Relay or a tunnel, test playback on cellular data with Wi-Fi disabled. Success means the stream starts without a port-forward rule. If it fails, disable Relay or remove the tunnel client and restart the Plex service to return to the previous state before trying another method.

If you need a controlled diagnosis of your exact setup,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
