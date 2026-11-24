---
title: "Plex Remote Streaming Buffering: Fix Relay Playback Stalls"
description: "Stop Plex remote streaming buffering when playback routes through relay. Follow these checks to confirm the cause and restore smooth playback."
seo_title: "Plex Remote Streaming Buffering: Fix Relay Playback Stalls"
seo_description: "Stop Plex remote streaming buffering when playback routes through relay. Follow these checks to confirm the cause and restore smooth playback."
keywords:
  - "plex remote streaming buffering"
date: 2026-11-24T12:08:01+08:00
publishDate: 2026-11-24T12:08:01+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are outside your home network, and Plex has switched to relay playback, but the video keeps buffering every few seconds.

## Confirm Relay Is the Active Path

Open the Plex client's playback info or dashboard while the stream is running. Look for "Relay" in the connection details. If it says "Indirect" or shows a relay server, that confirms the stream is not using a direct connection. A direct connection should show your server's public IP and port.

## Check the Relay Bandwidth Limit

In Plex Media Server, go to Settings > Network and find the relay setting. Note the relay bandwidth limit. If it is set to 1 Mbps or 2 Mbps, that is often too low for the video bitrate you are playing. Raise it to a higher value, such as 3 Mbps or more, then save. Retry the same video. If buffering stops, the limit was the cause.

## Test a Lower Bitrate

If raising the relay limit does not help, lower the remote streaming quality in the client to 2 Mbps or 1.5 Mbps. Play for two minutes. If it plays smoothly, your upload speed or relay capacity is the bottleneck. This is a **plex remote streaming buffering** issue tied to bandwidth, not a server fault.

## Verification Test

After any change, stop the stream, wait ten seconds, and start it again. Watch the playback info for thirty seconds. A stable relay stream should show no repeated buffering icon and steady progress. If it still buffers, note the exact relay limit and client quality setting you used.

## Rollback and Recovery

If raising the relay limit causes other remote users to slow down, return it to the previous value. Then set the client to a lower quality as a temporary workaround. For a controlled diagnosis of your specific network,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
