---
title: "VPN Split Tunneling Fix: When Plex Remote Access Is Green but Playback Fails"
description: "Plex remote access shows green but playback fails when a VPN is active. Learn how to check split tunneling, verify the connection, and restore remote playback."
seo_title: "Fix Plex Remote Access Green but Playback Fails with VPN"
seo_description: "Plex remote access shows green but playback fails when a VPN is active. Learn how to check split tunneling, verify the connection, and restore remote playback."
keywords:
  - "plex remote access not working with vpn"
date: 2026-11-24T08:05:55+08:00
publishDate: 2026-11-24T08:05:55+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You're outside your home network, Plex Remote Access shows green, but the remote client won't play anything—and you haven't yet run a controlled diagnosis.

## Check VPN split tunneling on the server

On the Plex server machine, open your VPN client and look for split tunneling or app exclusions. The Plex Media Server process must bypass the VPN so remote clients reach your home IP directly. If split tunneling is off, enable it and add Plex Media Server to the exclusion list. Result interpretation: if the VPN routes all traffic, Plex may still report green because the local check succeeds, but remote playback fails—this confirms the VPN is intercepting the stream.

## Confirm the public port and IP

In Plex Settings > Remote Access, note the public port. Then, from the remote client's network, test that port with a simple TCP check (for example, an online port tester). If the port shows closed while the VPN is active but open when the VPN is paused, the VPN is blocking inbound connections. This is a common form of **plex remote access not working with vpn**.

## Verification test

Pause the VPN on the server, restart Plex Media Server, and try playback from the remote client. If playback works with the VPN off, re-enable split tunneling with the Plex exclusion and test again. Success means playback starts without pausing the VPN.

## Rollback and recovery

If split tunneling causes other apps to fail, revert the VPN to full tunnel mode, restart Plex, and confirm remote access still shows green. Then reapply the exclusion carefully. If playback remains broken,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) before changing router or firewall rules.
