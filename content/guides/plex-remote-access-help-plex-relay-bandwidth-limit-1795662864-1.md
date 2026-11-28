---
title: "Plex Relay Buffering: Diagnose the Bandwidth Limit Before Blaming Your Connection"
description: "Remote Plex playback keeps buffering through relay? Learn how to check the relay bandwidth limit, interpret results, and verify a fix without guessing."
seo_title: "Plex Relay Bandwidth Limit: Fix Remote Playback Buffering"
seo_description: "Remote Plex playback keeps buffering through relay? Learn how to check the relay bandwidth limit, interpret results, and verify a fix without guessing."
keywords:
  - "plex relay bandwidth limit"
date: 2026-11-28T22:18:57+08:00
publishDate: 2026-11-28T22:18:57+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

Your Plex server works fine at home, but when you watch remotely, playback keeps buffering and the dashboard shows it's going through Plex Relay.

## Check the relay bandwidth limit first

Open Plex Web, go to Settings > Remote Access, and look at the relay status. If it says "Relay" or shows a yellow/orange indicator, your server is falling back to relay because direct remote access isn't working. Now check the **plex relay bandwidth limit**—by default, Plex Relay caps streams at 1 Mbps for free users and 2 Mbps for Plex Pass. That cap is often too low for the original file, causing constant buffering.

Interpretation: if the dashboard shows a stream bitrate above the relay cap, buffering is expected. If the bitrate is below the cap and still buffers, the relay itself is congested or your server's upload is the bottleneck.

## Run a controlled test

1. In the remote client, open the same video and set quality to 1 Mbps (or 2 Mbps if you have Plex Pass). Play for two minutes.
2. If buffering stops, the relay bandwidth limit is the cause. If it continues, note the server's upload speed and the relay region.
3. Next, disable relay temporarily (Settings > Network > uncheck "Enable Relay") and test direct remote access. If direct playback works, relay was the problem.

## Verify and recover

Re-enable relay after testing. For a permanent fix, set up port forwarding or use a VPN with direct access so relay isn't needed. If you changed quality settings, reset them to original after confirming the cause.

If you're still stuck at the relay buffering step,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) with your dashboard screenshot and test results.
