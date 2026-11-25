---
title: "CGNAT Blocks Plex Port Forwarding: What to Do Before You Diagnose"
description: "Stuck at the CGNAT blocks port forwarding step? Learn how to confirm CGNAT, interpret router results, and recover Plex remote access without a controlled diagnosis."
seo_title: "CGNAT Blocks Plex Port Forwarding: Practical Troubleshooting"
seo_description: "Stuck at the CGNAT blocks port forwarding step? Learn how to confirm CGNAT, interpret router results, and recover Plex remote access without a controlled diagnosis."
keywords:
  - "plex remote access port forwarding"
date: 2026-11-25T11:05:52+08:00
publishDate: 2026-11-25T11:05:52+08:00
draft: false
categories:
  - "Remote Access Troubleshooting"
category_slug: "remote-access-troubleshooting"
---

You are trying to set up **plex remote access port forwarding**, but your router cannot expose the Plex port because your ISP uses CGNAT.

## Confirm the CGNAT condition

First, compare your router's WAN IP with the public IP seen by the internet. On the Plex server, open a browser and search for "what is my IP." Then log into your router and find its WAN or internet status page. If the router's WAN IP is in the 100.64.0.0/10 range, or it differs from the public IP, CGNAT is almost certainly present. A private WAN IP such as 192.168.x.x or 10.x.x.x behind another NAT also blocks port forwarding.

## Interpret the router result

When you try to add a Plex port forward, a CGNAT router may reject the rule, show no WAN IP to bind, or accept the rule but never receive inbound connections. If the rule saves but Plex still reports remote access as unavailable, do not keep changing ports. That result means the ISP layer is not delivering the port to your router.

## Run a verification test

From a device outside your home network, use an online port checker against your public IP and the Plex port. A closed or filtered result confirms the port is not reachable. Repeat the check after any change so you compare the same result.

## Recover and next step

Remove the unused port forward to avoid confusion, then ask your ISP for a public IPv4 address or switch to a connection that provides one. If that is not possible, use Plex Relay as a temporary fallback, noting it may limit quality. For a guided review,

![Phone playing a video beside a laptop during a Plex remote access test](/images/plex-service-test.webp "Plex remote access playback test")

[Ask for help](/#consult).
