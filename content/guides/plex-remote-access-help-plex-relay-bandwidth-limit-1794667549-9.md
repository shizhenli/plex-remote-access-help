---
title: "Plex Relay Bandwidth Limit: Stop Remote Playback Buffering"
description: "Remote Plex playback buffers because the relay's bandwidth limit is too low. Check your relay setting, interpret the cap, and verify with a controlled test."
seo_title: "Fix Plex Relay Bandwidth Limit Buffering (Remote Playback)"
seo_description: "Remote Plex playback buffers because the relay's bandwidth limit is too low. Check your relay setting, interpret the cap, and verify with a controlled test."
keywords:
  - "plex relay bandwidth limit"
date: 2026-11-24T11:06:02+08:00
publishDate: 2026-11-24T11:06:02+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

Your Plex server is outside the home network, playback is routing through relay, and it buffers repeatedly before you can finish a controlled diagnosis.

## Confirm the relay path and the cap

On the server, open Settings > Remote Access. If it says relay is in use, note the relay bandwidth value shown there. Then play the same file remotely and open the Now Playing dashboard. If the stream shows Indirect, you are on relay. Compare the file's bitrate (from the media info panel) with the relay value. If the bitrate is higher than the cap, buffering is expected, not a fault. That gap is the **plex relay bandwidth limit** at work.

## Adjust and interpret

In Settings > Remote Access, set the relay bandwidth to a value above the file's bitrate, or pick a lower-bitrate version for testing. Save, then restart the Plex Media Server service so the change applies. Replay the same file. If the dashboard still shows Indirect but playback now runs without repeated stalls, the cap was the cause. If it still buffers at a higher cap, the relay link itself is congested; note the time and stop there rather than changing more settings.

## Verification test

Play a short clip at a known low bitrate remotely. Watch the dashboard for two minutes. A steady Indirect stream with no buffering confirms the relay path is healthy at that bitrate. Then try the original file once; if it buffers again, the cap is still below its bitrate.

## Rollback and recovery

If raising the cap causes stutter elsewhere, return the relay bandwidth to its previous value and use a lower-bitrate version for remote viewing. For a guided review,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
