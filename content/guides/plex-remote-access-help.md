---
title: "Plex Remote Access Not Working: Diagnose the Path Before Changing Settings"
seo_title: "Plex Remote Access Not Working: Diagnose the Path"
description: "Plex remote access not working? Check remote video entitlements, CGNAT vs double NAT, direct/relay connections, Direct Play/transcoding, and client playback."
keywords:
  - "plex remote access not working"
  - "plex remote access"
categories:
  - "Remote Access Troubleshooting"
date: 2026-11-13
lastmod: 2026-11-13
---

**plex remote access not working**. 

<p>Plex remote access fails at one of four layers: the Plex account entitlement, the Plex host, the router/ISP path, or the client playback decision. Test them in that order. Do not change the library or reinstall Plex until you know which layer fails.</p>

<h2>1. Check the remote video entitlement first</h2>
<p>Before changing a router, check whether the affected client is allowed to play video remotely at all. Plex’s official requirements apply to personal video streamed outside the server’s local network. For an affected app, at least one of these must be true:</p>
<ul>
  <li>The Plex Media Server admin account has an active Plex Pass.</li>
  <li>Your Plex account has an active Plex Pass.</li>
  <li>Your account has an active Remote Watch Pass.</li>
</ul>
<p>The restriction applies to personal video, not music streamed to Plexamp or photos in Plex Photos. Plex currently lists Android and iOS mobile, PlayStation, Plex for Windows/Mac/Linux, Roku, supported smart TVs, the web app, and Xbox as affected platforms; more apps may enforce the requirement later. Check the account actually signed in on the client, not only the server owner’s account.</p>
<p>Official source: Requirements for Remote Playback of Personal Media. If the client is not entitled, fix the account/subscription first; port forwarding will not change the result. If it is entitled, continue to the network layers.</p>

<h2>2. Record the exact failure</h2>
<p>Open Plex Web → Settings → Remote Access. Write down the public address/port, whether it says Fully accessible, and the time. Then take the phone off Wi-Fi, use cellular, and try one title. “Works at home” is not a remote-access pass.</p>

<h2>3. Separate double NAT from CGNAT</h2>
<p>Double NAT is two NAT devices in your own path: for example, an ISP modem/router doing NAT and your own Wi-Fi router doing NAT again. The server’s router WAN address is a private address, but the internet sees a different public address. You can often fix this by putting one device in bridge mode or by forwarding the port through <em>both</em> NAT devices.</p>
<p>CGNAT is NAT operated by the ISP for many customers. Your router may show a WAN address in the shared carrier range <code>100.64.0.0/10</code> — specifically <code>100.64.0.0–100.127.255.255</code> — while the public internet address is different. Port forwarding on your router cannot fix CGNAT. Ask the ISP for a public IPv4 address, or use a private path such as Tailscale or Plex Relay.</p>
<p>Plex’s own troubleshooting article describes the same test: compare the router’s WAN/Internet address with the address shown by an external IP-check site. If they differ, suspect double NAT or CGNAT; a carrier-range address identifies CGNAT. Source: Plex: Troubleshooting Remote Access. The <code>100.64.0.0/10</code> range is defined in RFC 6598.</p>

<h2>4. Check connection type separately from playback type</h2>
<p>These are two different questions and must not be conflated:</p>
<ul>
  <li>Connection: Plex Dashboard may show <em>Direct</em> or <em>Indirect</em>. “Indirect” usually means the stream is going through Plex Relay (or another indirect path); it does not automatically mean the video is transcoding.</li>
  <li>Playback — Direct Play: the client supports the file container, video codec, audio codec, resolution, and bitrate, so the file is sent as-is without changing the media.</li>
  <li>Playback — Direct Stream: the client supports the video and audio streams but not the file container. The server extracts the original streams and repackages them into a compatible container on the fly. If only the container changes and the original video and audio streams are preserved, this is Direct Stream, not Transcode. A “partially transcoded direct stream” may convert only the audio while leaving the video untouched.</li>
  <li>Playback — Transcode: the client cannot handle the video or audio stream, so the server converts the incompatible track (and may also change resolution or bitrate). This is the CPU-intensive case.</li>
</ul>
<p>In Plex Dashboard → Now Playing, read the connection field and the playback decision as separate facts. A relayed stream can still be Direct Play; a direct connection can still be Direct Stream or Transcode because of container, codec, subtitle, or client limits. A green Remote Access page is not acceptance, and “Direct” is not the same as “Direct Play.”</p>
<p>Official definitions: Plex: Direct Play, Direct Stream, Transcoding Overview and Plex: Streaming Media — Direct Play and Direct Stream.</p>

<h2>5. Choose one path</h2>
<p>Tailscale: install it on the Plex host and the client, sign into the same tailnet, and browse to the host’s Tailscale IP on port 32400. This avoids router changes but requires the Tailscale app on the client.</p>
<p>Only run CLI commands on devices that actually provide a Tailscale command line: Windows, macOS, or Linux. Phones, tablets, TVs, and consoles use the app UI, not a shell. On a CLI-capable Plex host or client, verify the address and route with:</p>
<pre><code>tailscale ip -4
tailscale status
tailscale ping &lt;peer-name-or-tailscale-ip&gt;</code></pre>
<p>Use the <code>100.x.y.z</code> address returned by <code>tailscale ip -4</code> on the Plex host, and confirm the client appears in <code>tailscale status</code>. On a phone, use the Tailscale app’s device list and connection status instead. Tailscale CLI reference: Tailscale CLI documentation.</p>
<p>Port forward: only when the ISP gives a real public IPv4 address. Reserve the host IP, forward TCP 32400 to it, and set the same public port in Plex. Never expose the whole PC.</p>
<p>Reverse proxy: only when you need a hostname and HTTPS for several users. It adds DNS, certificate, and proxy layers; test it after the direct path works.</p>

<h2>6. Retest from outside</h2>
<p>Use cellular data, play for at least two minutes, and check Plex Dashboard → Now Playing. Record two separate fields:</p>
<ul>
  <li>Connection: Direct or Indirect.</li>
  <li>Playback: Direct Play, Direct Stream, or Transcode.</li>
</ul>
<p>Do not write “Direct” for both. A Direct connection with Direct Stream is a different result from Direct Play, and either can still be a problem if the client or network cannot sustain it. Also note the client app and account used. A green Remote Access page alone is not acceptance.</p>

<h2>7. Rollback</h2>
<p>Remove only the change you made: stop Tailscale, delete the one port-forward rule, or disable the proxy host. Confirm local playback still works. Keep a note of the original router/Plex values.</p>

<h2>Need help with your exact path?</h2>
<p>If the entitlement is active and the path is still unclear, send the Plex host OS, client device, connection type, playback type, and what happens on cellular. Do not send passwords.</p>
<p><a href="/#consult">Request a quote for your Plex setup</a></p>

<h2>Sources</h2>
<ul>
  <li>Plex: Requirements for Remote Playback of Personal Media</li>
  <li>Plex: Troubleshooting Remote Access</li>
  <li>Plex: Remote Streaming (Setting Up Remote Access)</li>
  <li>Plex: Direct Play, Direct Stream, Transcoding Overview</li>
  <li>Plex: Streaming Media — Direct Play and Direct Stream</li>
  <li>RFC 6598: Shared Address Space (100.64.0.0/10)</li>
  <li>Tailscale CLI documentation</li>
</ul>
