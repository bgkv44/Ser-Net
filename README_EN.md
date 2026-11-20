<p align="right">
  <a href="README.md">Русский</a> | <strong>English</strong>
</p>

<div align="center">

<h1>Ser-Net</h1>

<p><b>A Windows x64 VPN client built on Xray-core: subscriptions, smart routing and <code>sernet://</code> links.</b></p>

<p>
  <a href="https://github.com/bgkv44/Ser-Net/releases"><img alt="Release" src="https://img.shields.io/github/v/release/bgkv44/Ser-Net?include_prereleases&amp;label=release&amp;color=7ee0ad"></a>
  <a href="https://github.com/bgkv44/Ser-Net/releases"><img alt="Downloads" src="https://img.shields.io/github/downloads/bgkv44/Ser-Net/total?label=downloads&amp;color=82b8ff"></a>
  <img alt="Platform" src="https://img.shields.io/badge/platform-Windows%2010%20%7C%2011%20x64-0078D6?logo=windows&amp;logoColor=white">
  <img alt="Core" src="https://img.shields.io/badge/core-Xray--core-6f42c1">
  <img alt="Status" src="https://img.shields.io/badge/status-beta-ffd27d">
</p>

<p>
  <a href="https://github.com/bgkv44/Ser-Net/releases">Download</a> ·
  <a href="https://github.com/bgkv44/Ser-Net-android">Android</a> ·
  <a href="https://bgkv44.github.io/Ser-Net/">User guide</a> ·
  <a href="https://t.me/secureNet_Support_new">Support</a> ·
  <a href="README.md">Русский</a>
</p>

</div>

**Contents:** [About](#about) · [Android](#android-version) · [Screenshots](#screenshots) · [Features](#features) · [Protocols](#supported-protocols) · [Modes](#connection-modes) · [Routing](#routing) · [Install](#installation) · [First connection](#first-connection) · [Commands](#sernet-commands) · [Settings](#settings) · [Troubleshooting](#troubleshooting) · [Support](#support)

## About

Ser-Net is a Windows desktop VPN client built on [Xray-core](https://github.com/XTLS/Xray-core). It reads servers from a standard provider subscription link and lets you choose one of three modes: keep Russian sites direct, route all traffic through the VPN, or tunnel only the sites and applications you pick.

> [!NOTE]
> Ser-Net does not provide VPN servers, subscriptions or infrastructure access. You need your own compatible link or subscription from a provider.

## Android version

Ser-Net is also available for Android: a `VpnService` tunnel, per-app routing, a Quick Settings tile and the same subscriptions as on desktop.

- Repository and docs: [bgkv44/Ser-Net-android](https://github.com/bgkv44/Ser-Net-android)
- Download APKs: [releases page](https://github.com/bgkv44/Ser-Net-android/releases) — current version `1.0.0-beta.1.5`, builds for `arm64-v8a`, `armeabi-v7a`, `x86` and `x86_64`.

The Android build ships separately from Windows and keeps its own version line: its own app, service and versionCode.

## Screenshots

<p align="center">
  <img src="docs/screenshots/connection.png" alt="Connection screen: status, timer, speed and server list" width="880">
</p>

<p align="center"><em>Connection screen</em> — status, speed, IP and servers with latency. The public IP is hidden in the screenshot.</p>

<p align="center">
  <img src="docs/screenshots/settings.png" alt="Settings: connection mode, themes, logs and routing" width="880">
</p>

<p align="center"><em>Settings</em> — Smart mode is selected and pending changes are visible. Apply was not pressed. HWID and device name are hidden.</p>

## Features

| Feature | Details |
|---|---|
| **Subscriptions** | Several links at once, the active subscription's servers on the main screen, and per-card refresh without switching the others. |
| **Subscription data** | Traffic used, expiry date, HWID status and a provider dashboard button when the subscription exposes them. |
| **Server selection** | Search by name or country, TCP latency checks, an available-only filter, and fastest-server picking with confirmation. |
| **Routing** | Three modes, ready-made service presets, custom domains and IPs, list import and export. |
| **Tunnel modes** | System proxy without administrator rights, or TUN through the Ser-Net service for system-wide traffic. |
| **DPI evasion** | TLS fragmentation for TLS/REALITY profiles when connections are blocked by SNI. |
| **Automation** | Launch at Windows sign-in, auto-connect to the fastest server at startup, and `sernet://` links for shortcuts. |
| **Diagnostics** | Core and service logs, core version, service state and update checks inside the app. |

## Supported protocols

| Protocol | Support |
|---|---|
| VLESS | ✅ |
| VMess | ✅ |
| Trojan | ✅ |
| Shadowsocks | ✅ |

Hysteria2 is not supported: Xray-core does not work with it.

## Supported transports

TCP · WebSocket (WS) · gRPC · XHTTP · HTTP

The availability of a specific transport depends on the server configuration and its compatibility with Xray-core.

## Connection modes

| Mode | Behaviour |
|---|---|
| **System proxy** | Sets a local proxy in Windows settings. Works without administrator rights; apps that honour system proxy settings use it. |
| **TUN** | Brings up a virtual network interface and routes traffic for the whole system. Requires the installed Ser-Net service and a UAC confirmation during installation. |

## Routing

| Mode | Behaviour |
|---|---|
| **Smart** | Russian sites and the local network stay direct; everything else goes through the VPN. |
| **All traffic through VPN** | Everything is tunnelled except local networks and your exceptions. In system proxy mode it is labelled “Traffic through proxy”. |
| **Selected only** | Only rules in the “Through VPN” list are tunnelled; everything else stays direct. Ad-domain blocking works in this mode. |

On an active connection, changes are marked as pending and applied with the **Apply** button. If a subscription ships a ready-made JSON config, routing is controlled by the provider.

## Requirements

- Windows 10 or 11, 64-bit.
- A compatible Xray-core configuration.
- Your own connection link or subscription.
- For TUN: the Ser-Net service (installed from the app, requires a UAC confirmation).

## Installation

1. Open the [releases page](https://github.com/bgkv44/Ser-Net/releases).
2. Pick a file:
   - **Installer** `Ser-Net_..._x64-setup.exe` — regular system installation;
   - **Portable** `SerNet-...-windows-x64-portable.zip` — unpack anywhere and run without installing.
3. Launch Ser-Net.

Current builds are marked **beta**: test versions that may change between releases.

## First connection

1. Open **Subscriptions** in the bottom navigation.
2. Click **Add subscription**, paste the link and press **Load**. Pasting straight from the clipboard works too.
3. With several subscriptions, press **Select** on the one you need; its servers appear on the main screen.
4. On the **Connection** screen pick a server and press the round power button. Or press **Connect to fastest server**: the app checks the nodes and asks you to confirm.
5. Adjust the connection and routing modes in settings if needed.

## `sernet://` commands

Commands control the app from a shortcut, script or another application. Replace placeholders in braces with your own values.

| Command | Action |
|---|---|
| `sernet://connect` | Connect to the selected server, or start fastest-server picking when none is selected. |
| `sernet://open` | Show the window and connect if the VPN is not running. |
| `sernet://disconnect` | Disconnect the VPN. |
| `sernet://toggle` | Turn the VPN on if it is off, and vice versa. |
| `sernet://best` | Check servers and pick the fastest one. |
| `sernet://refresh` | Refresh the active subscription. |
| `sernet://add/{url}` | Add a subscription from a URL-encoded link. |
| `sernet://server/{name-or-country-code}` | Select a server by country code or part of its name. |
| `sernet://routing/off` | Return to Smart mode; manual rules are kept. |
| `sernet://routing/mode/smart` | Enable Smart mode. |
| `sernet://routing/mode/global` | Enable All traffic through VPN. |
| `sernet://routing/mode/selective` | Enable Selected only. |
| `sernet://routing/add/{base64}` | Import rules from base64url: JSON arrays `proxy`/`direct`/`block`, or a plain list. |

The in-app reference with copy buttons lives under **Settings → Ser-Net commands**.

## Settings

- **Connection mode** — system proxy or TUN; applied on the next connection.
- **Ser-Net service** — state, install, update and reinstall.
- **Autostart** — launch at Windows sign-in without a UAC prompt.
- **Protect traffic at startup** — on the next launch the app checks servers and connects to the fastest one.
- **Appearance** — light, dark or system theme.
- **Logs** — core and service journals for diagnostics.
- **Updates** — built-in version checks plus a manual check under About.

> [!WARNING]
> A subscription URL is access to your account. Do not post it in chats or attach it to issues. Logs without the link are enough for diagnostics.

## Troubleshooting

- **No servers appeared** — check the subscription link and press “Refresh”. A failed download keeps the previous list.
- **Cannot connect** — try another server and check the connection mode. For TUN, make sure the Ser-Net service is installed.
- **A site takes the wrong route** — check the mode, the relevant rule list, and apply pending changes.
- **Need details** — open “Settings” → “Logs”, copy the journal and attach it to your report.

## Support

- User guide: [bgkv44.github.io/Ser-Net](https://bgkv44.github.io/Ser-Net/)
- Telegram: [@secureNet_Support_new](https://t.me/secureNet_Support_new)
- Bugs and ideas: [GitHub Issues](https://github.com/bgkv44/Ser-Net/issues)

Include the version from About and attach logs. Never send your subscription link or passwords.

## Source code

This repository publishes ready-to-use builds, documentation and the user guide. Application source code is not hosted here, so the program cannot be built from this repository — use the files on the [releases page](https://github.com/bgkv44/Ser-Net/releases).

## Important

Check the legal requirements in your jurisdiction before using or distributing the program. Do not use or distribute it where it is prohibited or restricted by applicable law.

---

<div align="center">
  <sub>Ser-Net · <a href="#">Back to top</a> · <a href="README.md">Русская версия</a> · <a href="https://github.com/bgkv44/Ser-Net/releases">Releases</a></sub>
</div>