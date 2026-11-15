---
title: "Plex Remote Access Not Working with VPN: Green Status but Playback Fails"
description: "Troubleshoot Plex remote access showing green with a VPN but playback fails. Step-by-step checks for VPN split tunneling, port forwarding, and verification."
seo_title: "Plex Remote Access Not Working with VPN: Fix Green Light, No Playback"
seo_description: "Troubleshoot Plex remote access showing green with a VPN but playback fails. Step-by-step checks for VPN split tunneling, port forwarding, and verification."
keywords:
  - "plex remote access not working with vpn"
date: 2026-11-15T18:57:02+08:00
publishDate: 2026-11-15T18:57:02+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You're running Plex behind a VPN, remote access shows green, but remote clients can't play anything.

## Check VPN Split Tunneling

Your VPN may be routing Plex traffic through a tunnel that blocks inbound connections. Open your VPN client and enable split tunneling so Plex Media Server bypasses the VPN. On Windows, add Plex Media Server.exe to the exclusion list. On Linux, use policy routing to exclude the Plex process. After applying, restart Plex. Result interpretation: if remote access stays green and playback starts working, split tunneling was the cause. If it turns red, your VPN is still intercepting traffic.

## Verify Port Forwarding on the VPN Interface

If your VPN assigns a shared IP (common with commercial VPNs), inbound port forwarding won't work. Check your VPN provider's documentation for dedicated IP or port forwarding support. In Plex, go to Settings > Remote Access and manually specify a port. Then forward that port on your router to the VPN interface IP, not the local LAN IP. Result interpretation: Plex shows green only when it can reach the public IP and port. If it stays green but playback fails, the VPN may be dropping the return traffic.

## Test with a Controlled Client

Disconnect the VPN on your server temporarily. From a remote network (mobile hotspot), try playing a small video. If playback works without VPN, the VPN configuration is the culprit. Re-enable the VPN and test again. This isolates whether **plex remote access not working with vpn** is due to tunnel routing or port blocking.

## Rollback and Recovery

If changes break local access, revert split tunneling and port forwarding to previous settings. Restart Plex and your router. Document the working configuration before making further changes.

If these steps don't resolve it,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) with your VPN logs and Plex remote access screenshot.
