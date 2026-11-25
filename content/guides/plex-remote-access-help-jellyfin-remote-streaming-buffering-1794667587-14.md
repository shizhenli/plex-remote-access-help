---
title: "Jellyfin Remote Streaming Buffering Through Relay: A Step-by-Step Diagnosis"
description: "Remote Jellyfin playback buffers when routed through relay. Follow these checks to diagnose and restore smooth playback."
seo_title: "Fix Jellyfin Remote Streaming Buffering via Relay"
seo_description: "Remote Jellyfin playback buffers when routed through relay. Follow these checks to diagnose and restore smooth playback."
keywords:
  - "jellyfin remote streaming buffering"
date: 2026-11-25T09:05:57+08:00
publishDate: 2026-11-25T09:05:57+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are outside your home network, trying to watch something on Jellyfin, and the stream keeps pausing to buffer because it is going through a relay instead of a direct connection. This is a common symptom of **jellyfin remote streaming buffering**, and it usually points to a relay bottleneck rather than a problem with your media files. Let's work through it methodically.

## Check the Relay Status

First, confirm that playback is actually using the relay. In Jellyfin, open the dashboard while a remote stream is active. Look at the active streams section and note whether the connection shows as "relay" or "direct." If it says relay, that confirms the path. Next, check your server's remote access settings. The relay has a bandwidth limit, often 1–2 Mbps by default. If your media bitrate exceeds that, buffering is expected. Lower the remote streaming quality in the client to match or fall below the relay limit, then test again. If buffering stops, the relay bandwidth was the cause.

## Verify Direct Connection Possibility

If lowering quality is not acceptable, you need a direct connection. Check whether your router has UPnP enabled or a manual port forward for Jellyfin's port. Also verify that your ISP is not using CGNAT, which blocks inbound connections. A quick test: from outside, try accessing your server's public IP and port directly. If it fails, direct connection is not available, and the relay is your only fallback.

## Verification Test

After any change, play a remote video for at least two minutes. Watch the dashboard: if the stream shows direct and playback is smooth, the fix worked. If it still shows relay and buffers, the relay limit is still the constraint.

## Rollback Note

If you changed port forwarding or UPnP settings and remote access breaks entirely, revert those changes and confirm the relay still works as a fallback before continuing.

If these steps do not resolve the buffering,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) for a focused review of your setup.
