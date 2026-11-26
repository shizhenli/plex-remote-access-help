---
title: "CGNAT Is Blocking Your Plex Port Forward: What to Check Before You Change Anything"
description: "Plex remote access behind CGNAT stops port forwarding cold. Confirm the block, test the result, and recover safely without guessing."
seo_title: "Plex Remote Access Behind CGNAT: Port Forwarding Blocked Fix"
seo_description: "Plex remote access behind CGNAT stops port forwarding cold. Confirm the block, test the result, and recover safely without guessing."
keywords:
  - "plex remote access behind cgnat"
date: 2026-11-26T10:05:02+08:00
publishDate: 2026-11-26T10:05:02+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You set up port forwarding for Plex, but the router cannot expose the Plex port because your ISP uses CGNAT.

## Confirm the CGNAT block

Open your router's status page and find the WAN IPv4 address. Then visit a public IP-check page from a device on the same network and note the address it shows.

- If the router WAN address is in 100.64.0.0/10, you are behind CGNAT.
- If the router WAN address matches the public address, CGNAT is not the cause and you should stop here.
- If the router WAN address is a normal public address but differs from the check page, carrier-grade NAT is still likely.

This is the step where **plex remote access behind cgnat** usually stalls: the port-forward rule looks correct, but the ISP never routes inbound traffic to your router.

## Test the result

With the Plex port-forward rule in place, ask a device on cellular data (not your home Wi-Fi) to open your public address and Plex port. A connection timeout or refusal confirms the port is not reachable from outside. A successful connection means CGNAT is not blocking that port.

## Recover without breaking remote access

Do not delete your existing port-forward rule yet. Record the current Plex remote access settings, then try these in order:

1. Ask your ISP whether a public or static IPv4 address is available on your plan.
2. If not, use a relay or tunnel service that does not require inbound port forwarding.
3. Recheck Plex remote access after each change.

If a change makes things worse, restore the settings you recorded and re-test locally before continuing. For a guided diagnosis of your exact setup,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
