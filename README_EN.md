<p align="right">
  <a href="README.md">Русский</a> | <strong>English</strong>
</p>

# Ser-Net

**Ser-Net** is a VPN client for Windows x64 based on [Xray-core](https://github.com/XTLS/Xray-core).

The application allows users to import connection configurations and subscriptions, manage connections, select servers based on latency measurements, and monitor connection status and network traffic statistics.

## Features

- **Configuration Import** — import individual connection links and subscriptions.
- **Server Selection** — measure server latency and sort servers based on test results.
- **Connection Management** — connect, disconnect, and switch between servers.
- **Traffic Statistics** — monitor connection status and network activity.
- **System Proxy** — route traffic from supported applications through the selected server using Windows system proxy settings.
- **TUN Mode** — route network traffic through a virtual network interface.
- **Flexible Routing** — choose between routing all supported traffic through the proxy or connecting directly to local and selected Russian IP addresses.

## Supported Protocols

| Protocol | Support |
|---|---|
| VLESS | ✅ |
| VMess | ✅ |
| Trojan | ✅ |
| Shadowsocks | ✅ |

## Supported Transports

- TCP
- WebSocket (WS)
- gRPC
- XHTTP
- HTTP

The availability of each transport depends on the server configuration and its compatibility with Xray-core.

## Windows Connection Modes

### System Proxy

Uses the Windows system proxy settings to route traffic from supported applications through the selected server.

### TUN Mode

Uses a virtual network interface to route network traffic through the VPN tunnel.

**Important:** TUN mode requires the `SerNetService` Windows service to be installed and running.

## Routing

Ser-Net supports the following routing modes:

- **Global** — all supported traffic is routed through the selected server.
- **Direct** — local and selected Russian IP addresses are accessed directly, while all other traffic is routed through the server.

Actual routing behavior depends on the configured routing rules and connection settings.

## Requirements

- Windows 10 / 11 (x64).
- A compatible Xray-core configuration.
- Your own compatible connection link or subscription.
- For TUN mode: the `SerNetService` Windows service and the required system components.

## Getting Started

1. Install and launch Ser-Net.
2. Import a connection link or subscription.
3. Wait for the server list to load.
4. Select a server.
5. Choose a connection mode.
6. Click the Connect button.

## Server Infrastructure

Ser-Net works with servers compatible with Xray-core.

**Ser-Net does not provide VPN servers, subscriptions, connection configurations, or access to server infrastructure.** You must have your own compatible connection link or subscription to use the application.

## Legal Notice

Before using or distributing this software, check the applicable laws and regulations in your jurisdiction.

Do not use or distribute this software in jurisdictions where such use or distribution is prohibited or restricted by applicable law.

---

**Ser-Net** is client software designed to manage connections to compatible Xray-core infrastructure.
