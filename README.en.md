# Quasar — a free client for V2Board / Xboard / PPanel

**Quasar is a free white-label proxy client for service operators.** It talks to **V2Board, Xboard and PPanel** panels, runs on **Windows, macOS, Linux, Android and Android TV**, ships with a choice of kernels — **sing-box + xray**, **mihomo (Clash.Meta)** or **mihomo Smart** — and comes with **6 UI skins**. No build environment needed: fill in your brand online and get installers under your own name. **Signing up and building are free.**

The client is written in **Rust (Tauri 2)**, the interface in **TypeScript + React**, and the Android VPN service in **Kotlin**. The **bridge between the interface and the kernels is our own code** — config generation, starting and controlling the kernels, and panel integration all live there; it is not a fork of an existing client.

**Build yours online, free: <https://console.quasarapp.net/>**

[中文](README.md)

![Quasar client, six skins: Neon, Minimal, Tiles, iOS style, Glass, Dashboard](images/overview.png)

## Free

- **The client is free** — for operators to use and for end users to install.
- **Building is free** — console accounts are handed out by a Telegram bot at no cost; sign in and build installers under your own brand.
- **How**: open <https://console.quasarapp.net/>, follow "去 Telegram 机器人注册" on the sign-in page and send `/start` to the bot. Free accounts must stay in the official Telegram channel and group to build.

## Who it is for

- **Operators** who want a client carrying their own brand and wired to their own panel, without maintaining a codebase.
- **V2Board / Xboard / PPanel users**: instead of importing a subscription link into a third-party app, users **sign in with their panel account** — plans, traffic, nodes and tickets live in one app.

## Six skins

Pick one at build time, plus a brand colour. **Desktop and phone share one interface**: on a computer it is a resizable portrait window, so users switching devices find everything in the same place. Every skin supports light / dark / pure black. In each image: the desktop window on the left, then the home screen in the other theme, the node list and the plans page.

| Skin | Look |
|---|---|
| **Neon** (default) | Dark, a large glowing connect button |
| **Minimal** | Light grouped lists, like a system settings page |
| **Tiles** | Rounded tiles, the brand colour front and centre |
| **iOS style** | Large title, round power button, widgets |
| **Glass** | Translucent panes over a colour field |
| **Dashboard** | Dark, live throughput chart, monospaced figures |

![Neon skin](images/ui-neon.png)
![Minimal skin](images/ui-minimal.png)
![Tiles skin](images/ui-tiles.png)
![iOS style skin](images/ui-ios.png)
![Glass skin](images/ui-glass.png)
![Dashboard skin](images/ui-dash.png)

> Accounts, nodes, plans and traffic in the screenshots are demo data.

## Features

**Account and plans (straight from the panel)**
- Sign in, register, reset password with the panel account
- Plans, checkout, orders; balance top-up and gift cards where the panel has them
- Data left and expiry on the home screen, with renewal reminders
- Invites, tickets, announcements
- Knowledge base: Markdown / HTML / plain text, with tables, code highlighting and callouts
- Traffic log, signed-in devices
- The subscription is fetched and applied automatically; **the subscription URL is never shown**

**Nodes and connection**
- Search, favourites, sort by latency or name, one-tap latency test
- Auto select (by latency) and failover
- mihomo Smart: per-connection node selection, with the learned ranking on the node page
- Rule / Global / Direct modes; TUN mode and system-proxy mode
- Automatic reconnect
- **Honest status**: connected but nothing gets out is shown as such
- A hint when the exit country differs from the node's name

**Routing and network**
- Custom rules with bundled geo rule sets
- Ad blocking, block QUIC, LAN direct, allow LAN devices
- DNS settings, Fake-IP
- Per-app proxy (Android), campus-network mode
- Chained proxy / landing node, custom nodes (operator switch)

**Staying reachable**
- **Self-healing subscription**: a built-in TLS-fragment retry (zero config), then operator-supplied rescue nodes, then the last good subscription
- Several panel endpoints, fastest one used, automatic failover
- Bundled xray engine for REALITY, XTLS-Vision, xHTTP

**Tools**: speed test, exit IP and streaming-unlock check, live connections, redacted diagnostic log export

**For operators**
- Brand name, icon, colour, skin, login-page copy, default language and theme
- Live-chat support: Crisp, Chatwoot, SalesSmartly or a custom link
- Home shortcuts and an app-download list
- Default rules, DNS and test URLs **change from the console without rebuilding**; the config is a plain JSON file, optionally encrypted

## Panels

| Feature | V2Board | Xboard | PPanel |
|---|:---:|:---:|:---:|
| Sign in / register / plans / orders | ✅ | ✅ | ✅ |
| Announcements / knowledge base / tickets / invites | ✅ | ✅ | ✅ |
| Balance top-up | ✅ | — | ✅ |
| Gift cards | ✅ | ✅ | — |
| Traffic log | ✅ | ✅ | — |
| Signed-in devices | ✅ | ✅ | ✅ |

"—" means the panel has no such API.

## Kernels and protocols

- **sing-box + xray** (default) — sing-box is the main kernel; the bundled xray carries transports sing-box lacks, such as xHTTP
- **mihomo** — the Clash.Meta kernel, built from a pinned source release
- **mihomo Smart** — mihomo with per-connection smart node selection

Protocols: VMess, VLESS (REALITY / XTLS-Vision / xHTTP), Trojan, Shadowsocks, Hysteria, Hysteria2, TUIC, AnyTLS, SOCKS5, HTTP; WireGuard on the mihomo kernels.

## Built with

| Part | Language / framework |
|---|---|
| Client core (connection, config generation, panel integration) | **Rust**, on Tauri 2 |
| Interface (shared by desktop, phone and TV) | **TypeScript + React**, Tailwind CSS |
| Android VPN service and system integration | **Kotlin** |
| Proxy kernels (sing-box / mihomo / xray) | **Go** — upstream open-source projects |

Not Electron and not Flutter: the interface renders in the system WebView, so installers do not ship a browser engine.

## Build your own

1. Open **<https://console.quasarapp.net/>** — no account yet? Get one free from the Telegram bot linked on the sign-in page
2. Create a brand: name, panel type (V2Board / Xboard / PPanel), panel URL, icon
3. Pick a skin, a brand colour and a kernel
4. Choose platforms (Windows / macOS / Linux / Android / Android TV) and build
5. Download the installers and hand them to your users

Desktop is the most mature; Android and Android TV are newer targets.
