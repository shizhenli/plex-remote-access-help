---
title: "Plex Remote Access Shows Green but Playback Fails: Diagnose the Relay vs. Direct Connection"
description: "Plex shows remote access is green, but the remote client cannot play. Learn how to diagnose whether playback is using Plex Relay instead of a direct connection, and restore playback."
seo_title: "Plex Remote Access Green but Playback Fails: Fix Relay vs. Direct"
seo_description: "Plex shows remote access is green, but the remote client cannot play. Learn how to diagnose whether playback is using Plex Relay instead of a direct connection, and restore playback."
keywords:
  - "plex remote access not working"
date: 2026-11-25T12:05:54+08:00
publishDate: 2026-11-25T12:05:54+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You see the green checkmark in Plex settings, but when you try to play a video from outside your home network, it buffers forever or fails. This is a common form of **plex remote access not working**: the status indicator only confirms Plex's reachability check, not that media streams can flow directly to your client.

## Check whether playback is using Plex Relay

On the Plex server, open Settings > Remote Access and note the public port shown. Then, on the remote client, start a video and open the Now Playing dashboard on the server. Look at the connection type for that stream.

- If it says Indirect or Relay, your server is reachable through Plex's relay service, but direct playback is blocked. This explains why the status is green while playback fails.
- If it says Direct or Secure, the connection is direct and the issue is likely client-side or bandwidth-related.

## Confirm port forwarding and firewall

On your router, verify the port forward rule matches the public port in Plex exactly, and that it targets the server's current LAN IP. On the server, confirm the firewall allows inbound TCP on that port. A green status can persist even when the forwarded port is closed because Plex falls back to relay.

## Verification test

Disable Relay in Plex Settings > Network (set Relay to disabled), then retry playback from the remote client. If the stream now fails immediately instead of buffering, the direct path is still blocked. Re-enable Relay afterward as a temporary fallback.

## Rollback and recovery

If changes make remote access unavailable entirely, restore the previous port forward rule and re-enable Relay to regain basic connectivity. If direct playback still fails after these checks,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) with your server logs and the connection type shown in Now Playing.
