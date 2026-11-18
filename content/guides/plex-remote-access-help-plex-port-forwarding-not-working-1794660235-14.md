---
title: "Plex Port Forwarding Not Working: CGNAT Blocks the Port — What to Check Before You Recover"
description: "Plex port forwarding not working because your ISP uses CGNAT? Follow these checks to confirm the block, test remote access, and recover without wasting time on router rules."
seo_title: "Plex Port Forwarding Not Working: CGNAT Blocks the Port"
seo_description: "Plex port forwarding not working because your ISP uses CGNAT? Follow these checks to confirm the block, test remote access, and recover without wasting time on router rules."
keywords:
  - "plex port forwarding not working"
date: 2026-11-18T08:06:00+08:00
publishDate: 2026-11-18T08:06:00+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You set up a port forward for Plex, but remote access still fails, and you suspect your ISP's CGNAT is blocking the port before you can finish a controlled diagnosis.

## Confirm the CGNAT block

Open your router's status page and note the WAN IP. Then visit a public IP-check site from a device on the same network and compare. If the router WAN address is in a private range (10.x.x.x, 172.16-31.x.x, 192.168.x.x) or differs from the public address, your ISP is likely using CGNAT. Also check the Plex remote access page: if it shows a private or carrier-grade address and the manual port never turns green, the forward cannot work.

## Rule out a local mistake

Temporarily disable any firewall rule that blocks the Plex port, confirm the server's LAN IP is static, and verify the forward targets that exact IP and TCP port. Recheck Plex's manual port setting. If these are correct and the WAN address is still private, stop changing router rules — this is the CGNAT symptom, not a Plex configuration error.

## Verification test

From outside your home network (mobile data, no VPN), open the Plex app or a browser to your server's remote address. A timeout or refusal confirms the port is unreachable. Repeat after any change; do not rely on the green indicator alone.

## Recovery and rollback

If you added test forwards or firewall exceptions, remove them and restore your previous router settings. Then contact your ISP and ask for a public IPv4 address or CGNAT exemption; if unavailable, use Plex Relay as a temporary fallback. For a guided diagnosis,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).

If **plex port forwarding not working** persists after a public IP is assigned, recheck the forward and retest from mobile data.
