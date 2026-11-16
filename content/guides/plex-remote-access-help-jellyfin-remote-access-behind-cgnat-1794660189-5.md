---
title: "Jellyfin Remote Access Behind CGNAT: When Port Forwarding Is Blocked"
description: "Jellyfin remote access behind CGNAT fails because your router cannot expose the port. Learn to confirm CGNAT, test reachability, and recover without breaking local access."
seo_title: "Jellyfin Remote Access Behind CGNAT: Fix Port Forwarding Block"
seo_description: "Jellyfin remote access behind CGNAT fails because your router cannot expose the port. Learn to confirm CGNAT, test reachability, and recover without breaking local access."
keywords:
  - "jellyfin remote access behind cgnat"
date: 2026-11-16T10:05:43+08:00
publishDate: 2026-11-16T10:05:43+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You set up Jellyfin for remote viewing, but your router will not forward the port because your ISP uses CGNAT. Here is how to confirm that and recover.

## Confirm CGNAT Is the Blocker

Open your router's status page and note the WAN IPv4 address. Then visit a public IP-check page from a device on the same network and note the public address. If the WAN address falls in 100.64.0.0/10 (100.64.x.x through 100.127.x.x), or if it differs from the public address, CGNAT is almost certainly blocking port forwarding. In that case, no router port-forward rule will expose Jellyfin to the internet.

## Run a Reachability Test

From outside your home network (mobile data, not Wi-Fi), try to open your Jellyfin address and port. If it times out while local access still works, the port is not reachable from the internet. This confirms the failure is upstream, not a Jellyfin setting.

## Recover Without Breaking Local Access

Do not keep changing router rules; they cannot override CGNAT. Instead, use a solution that does not require an inbound port: a mesh VPN such as Tailscale or ZeroTier, or a reverse tunnel. Install the client on the Jellyfin host and on the remote device, then connect through the private address. If you must keep the old port-forward rule, note it first so you can restore it if your ISP later provides a public IP.

## Verify the Fix

Disconnect from Wi-Fi and open Jellyfin through the new private address. If the library loads and playback starts, remote access is restored. If it still fails, the tunnel or client is misconfigured.

For a controlled diagnosis of your exact setup,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult). This **jellyfin remote access behind cgnat** issue is common, and the checks above separate ISP limits from server misconfiguration.
