---
title: "Plex Relay Not Working: Stop Relay Playback Buffering"
description: "Troubleshoot Plex relay playback buffering with step-by-step checks, exact result interpretation, and a verification test to restore smooth remote streaming."
seo_title: "Fix Plex Relay Buffering: Diagnose Relay Playback Issues"
seo_description: "Troubleshoot Plex relay playback buffering with step-by-step checks, exact result interpretation, and a verification test to restore smooth remote streaming."
keywords:
  - "plex relay not working"
date: 2026-11-16T12:20:30+08:00
publishDate: 2026-11-16T12:20:30+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are watching a remote Plex stream, and it keeps buffering through the relay, leaving you stuck before you can finish a proper diagnosis. This article walks you through a controlled check to confirm whether the relay itself is the bottleneck and what to adjust.

## Check Relay Bandwidth and Server Load

First, open Plex Web on the server, go to Settings > Remote Access, and note whether relay is enabled. Then, on the client, start playback and open the Now Playing dashboard. Look at the stream details: if it says "Relay" and the bandwidth is capped near 1–2 Mbps, that confirms relay is active. Next, check the server's CPU and upload usage during playback. If the server is maxed out or your home upload is saturated, relay will buffer regardless of settings. Interpret a relay stream at 1 Mbps with low server load as a relay bandwidth limit, not a network fault.

## Adjust Relay Quality and Test

In Settings > Remote Access, click "Disable Relay" temporarily to see if direct play works. If direct play also buffers, the issue is your upload speed or port forwarding. If direct play is smooth, relay is the weak link. Re-enable relay and lower the remote video quality in the client to 720p or 2 Mbps. Then run a verification test: play a 5-minute clip and watch the Now Playing dashboard for consistent bandwidth above 1.5 Mbps without stalls. If it still buffers, note the exact relay bitrate shown.

## Rollback and Recovery

If changes make things worse, re-enable relay and reset the client quality to original. Document the relay bitrate you observed. For a guided diagnosis of your specific **plex relay not working** scenario,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
