---
title: "Plex Remote Access Not Working: Diagnose the Path Before Changing Settings"
seo_title: "Plex Remote Access Not Working: Diagnose the Path"
description: "Plex remote access not working? Diagnose CGNAT, closed ports, relay, Tailscale, and client playback with a repeatable test and rollback path."
keywords:
  - "plex remote access not working"
  - "plex remote access"
date: 2026-11-13
---
<p>Plex remote access fails at one of four layers: the Plex host, the router/ISP path, the Plex relay, or the client network. Test the path in that order. Do not change the library or reinstall Plex until you know which layer fails.</p>
<h2>1. Record the exact failure</h2>
<p>Open Plex Web → Settings → Remote Access. Write down the public address/port, whether it says Fully accessible, and the time. Then take the phone off Wi-Fi, use cellular, and try one title. “Works at home” is not a remote-access pass.</p>
<h2>2. Separate CGNAT from a closed port</h2>
<p>Compare the WAN address in the router with the public address Plex reports. If they differ, or the WAN address is in a carrier NAT range, port forwarding will not work. Do not keep changing firewall rules. Test a private path such as Tailscale, or use Plex Relay as a temporary fallback.</p>
<h2>3. Choose one path</h2>
<p><strong>Tailscale:</strong> install it on the Plex host and the phone, sign into the same tailnet, and browse to the host’s Tailscale IP:32400. This avoids router changes but requires the client app.</p>
<p><strong>Port forward:</strong> only when the ISP gives a real public IPv4 address. Reserve the host IP, forward TCP 32400 to it, and set the same public port in Plex. Never expose the whole PC.</p>
<p><strong>Reverse proxy:</strong> only when you need a hostname and HTTPS for several users. It adds DNS, certificate, and proxy layers; test it after the direct path works.</p>
<h2>4. Retest from outside</h2>
<p>Use cellular data, play for at least two minutes, and check Plex Dashboard → Now Playing. Record whether the stream is direct, indirect, or transcoding. A green Remote Access page alone is not acceptance.</p>
<h2>5. Rollback</h2>
<p>Remove only the change you made: stop Tailscale, delete the one port-forward rule, or disable the proxy host. Confirm local playback still works. Keep a note of the original router/Plex values.</p>
