---
title: "Plex Remote Access Green but Playback Fails with VPN: Fix the Split-Tunnel Leak"
description: "Plex shows remote access green but playback fails when a VPN is active. Learn how to check split tunneling, verify the public port, and restore playback without breaking your VPN."
seo_title: "Plex Remote Access Not Working with VPN: Green Status but Playback Fails"
seo_description: "Plex shows remote access green but playback fails when a VPN is active. Learn how to check split tunneling, verify the public port, and restore playback without breaking your VPN."
keywords:
  - "plex remote access not working with vpn"
date: 2026-11-18T10:23:28+08:00
publishDate: 2026-11-18T10:23:28+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are outside your home network, Plex Remote Access shows green, but the remote client cannot start playback while your VPN is connected. This usually means the VPN is intercepting the Plex traffic path even though the status check succeeds.

## Confirm the VPN is the variable

On the remote client, disconnect the VPN and retry the same title. If playback starts, the VPN is the cause. If it still fails, stop here and treat this as a separate remote-access issue.

## Check split tunneling on the server

On the Plex server machine, open your VPN client and look for split tunneling or an exclusion list. Add the Plex Media Server process and the local Plex port to the exclusion list. Also exclude the server's LAN subnet so local discovery is not routed through the tunnel. Save and restart Plex Media Server. Result interpretation: if the remote access page still shows green and the client plays after reconnecting the VPN, the leak is closed. If the status turns red, the VPN is now blocking the port and you need to allow the Plex port through the VPN firewall.

## Verify the public port from outside

From the remote client with the VPN on, use a port-checking tool against your public IP and the port shown in Plex Remote Access. A closed result means the VPN is still capturing that port. Recheck the exclusion entry for the exact port number.

## Rollback note

If playback still fails after these changes, remove the split-tunnel exclusions and restart the VPN to return to your previous state before trying another fix. For a controlled diagnosis of **plex remote access not working with vpn**,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
