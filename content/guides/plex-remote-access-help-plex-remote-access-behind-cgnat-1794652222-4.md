---
title: "CGNAT Blocks Plex Port Forwarding: Diagnose and Recover"
description: "Learn how to confirm CGNAT is blocking your Plex port forwarding, interpret router and ISP results, and recover remote access with a controlled workaround."
seo_title: "Fix Plex Remote Access Behind CGNAT: Port Forwarding Blocked"
seo_description: "Learn how to confirm CGNAT is blocking your Plex port forwarding, interpret router and ISP results, and recover remote access with a controlled workaround."
keywords:
  - "plex remote access behind cgnat"
date: 2026-11-14T19:38:03+08:00
publishDate: 2026-11-14T19:38:03+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You're setting up Plex remote access and the router won't let you forward the Plex port because your ISP uses CGNAT, leaving you stuck before any controlled diagnosis.

## Confirm the CGNAT block

Open your router's WAN status page and note the IP address. Then visit a public IP checker from a device on the same network. If the router WAN IP is in the 100.64.0.0/10 range, or it differs from the public IP, CGNAT is almost certainly the cause. A private WAN address such as 10.x.x.x or 192.168.x.x also confirms you are not receiving a public IPv4 address.

## Check the Plex side

In Plex, go to Settings > Remote Access. If it shows "Not available outside your network" and the manual port field cannot be reached from outside, the port forward is not taking effect. This is expected when the ISP gateway sits between you and the internet. Do not keep changing Plex settings; the failure is upstream.

## Verification test

From a mobile device on cellular data, open a browser and try to reach your Plex server using your public IP and the chosen port. If the connection times out, CGNAT is blocking inbound traffic. Repeat after any change; a successful load or Plex login page means the port is reachable.

## Recovery and workaround

Roll back any recent router port-forward rules you added for Plex to avoid conflicts. Then contact your ISP and ask for a public IPv4 address or CGNAT exemption; note the request date. If that is unavailable, use Plex Relay as a temporary fallback, accepting lower quality, or set up a VPN with port forwarding. For a guided diagnosis of your exact setup,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).

Remember: **plex remote access behind cgnat** cannot be fixed by router settings alone until the ISP provides a public address or you use a relay or VPN.
