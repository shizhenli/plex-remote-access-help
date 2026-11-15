---
title: "Plex Relay Bandwidth Limit: Why Remote Playback Buffers and How to Fix It"
description: "Remote Plex playback buffers through relay because the relay bandwidth limit caps throughput. Learn how to check the limit, interpret results, and verify a fix."
seo_title: "Plex Relay Bandwidth Limit: Fix Remote Playback Buffering"
seo_description: "Remote Plex playback buffers through relay because the relay bandwidth limit caps throughput. Learn how to check the limit, interpret results, and verify a fix."
keywords:
  - "plex relay bandwidth limit"
date: 2026-11-15T18:57:02+08:00
publishDate: 2026-11-15T18:57:02+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

Your Plex server is accessed outside the home network, and remote playback keeps routing through relay and buffering repeatedly, leaving you stuck before you can complete a controlled diagnosis.

## Confirm the relay bandwidth limit is the cause

On the server, open Settings > Remote Access and note whether it shows relay enabled. Then play the same remote file and open the Now Playing dashboard. If the stream shows Indirect, relay is active. Next, check the **plex relay bandwidth limit** setting under Settings > Network (or Remote Access, depending on version). The default cap is often 1 Mbps for remote streams. If your media bitrate exceeds that cap, repeated buffering is expected. Interpret it this way: Indirect plus a bitrate above the cap means the relay is throttling you, not a disk or CPU fault.

## Run a controlled test

Lower the remote playback quality to 720p or 1 Mbps in the client and retry. If buffering stops at the lower bitrate, the cap is confirmed. Then temporarily raise the relay bandwidth limit in server settings, save, and retry the original quality. A smooth stream after raising the cap confirms the limit was the bottleneck. If buffering persists even at low bitrate, the relay path itself is congested; stop here and avoid further changes.

## Verify and recover

Re-run the same remote file at the original quality and watch the dashboard for at least two minutes. Stable playback with no repeated buffering means the fix holds. If raising the limit causes instability or your upload cannot support it, revert the setting to its previous value and keep clients on a lower remote quality. Document the original value before changing anything so rollback is one step.

If the relay still buffers after these checks,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult) with your dashboard readings and current limit value.
