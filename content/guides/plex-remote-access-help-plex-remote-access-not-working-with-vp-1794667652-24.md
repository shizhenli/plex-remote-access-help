---
title: "Plex Remote Access Green but Playback Fails with VPN: Fix the Split-Tunnel Gap"
description: "Plex shows remote access green but playback fails when a VPN is active. Learn the split-tunnel check, exact result interpretation, and a verification test to restore playback."
seo_title: "Plex Remote Access Not Working with VPN: Green Status but Playback Fails"
seo_description: "Plex shows remote access green but playback fails when a VPN is active. Learn the split-tunnel check, exact result interpretation, and a verification test to restore playback."
keywords:
  - "plex remote access not working with vpn"
date: 2026-11-28T21:51:11+08:00
publishDate: 2026-11-28T21:51:11+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

Your Plex server reports remote access is green, but a remote client still cannot play anything while a VPN is running on the server machine.

## Confirm the VPN is the variable

On the Plex server, note the current remote access status. Then temporarily disconnect the VPN client (not the whole network) and retest playback from the remote client. If playback works without the VPN, the tunnel is intercepting Plex traffic. Reconnect the VPN before continuing.

## Check split tunneling and adapter binding

Open the VPN client settings and look for split tunneling or an exclusion list. Add the Plex Media Server process and the local Plex port (usually 32400) to the exclusion list. If your VPN has a kill switch, confirm it is not forcing all traffic through the tunnel after you add exclusions. In Plex, go to Settings > Remote Access and confirm the public port shown matches the port your router forwards. If the VPN assigns a different outbound address, Plex may still show green because the local check passes, while remote clients reach a different path.

Interpretation: if the public port changes after reconnecting the VPN, the tunnel is rewriting your outbound identity. If the port stays the same but playback fails, the VPN is likely blocking inbound connections on that port.

## Verification test

From the remote client, play a short clip. Then, on the server, check Plex Settings > Remote Access again. A green status with successful playback means the exclusion is working. A green status with failed playback means the VPN still owns the route; disable the VPN's inbound blocking or switch to a VPN mode that permits port forwarding.

## Rollback note

If playback worsens after changing split-tunnel rules, remove the Plex exclusions, restart the VPN client, and retest. This returns you to the prior state so you can try a different configuration. For a controlled diagnosis of **plex remote access not working with vpn**,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
