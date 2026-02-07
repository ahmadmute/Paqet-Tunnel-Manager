# Paqet Tunnel Manager | [📄 فارسی](README.fa.md)

> Management script for **paqet**: a raw socket, KCP-based tunnel for firewall/DPI bypass.  
> Supports **Kharej (external)** and **Iran (client)** setups.

**Maintained by:** [ahmadmute](https://github.com/ahmadmute) · **Based on:** [Paqet](https://github.com/hanselime/paqet) (hanselime) · **Manager idea:** [behzadea12](https://github.com/behzadea12)

---

## Quick Start

Run on **both servers** as **root**:

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/ahmadmute/Paqet-Tunnel-Manager/main/paqet-manager.sh)
```

Then choose **option 0**, then **option 1** to install prerequisites.

---

## Table of Contents

* [Quick Start](#quick-start)
* [What's Improved / Optimizations](#whats-improved--optimizations)
* [Installation Steps](#installation-steps)
  * [Step 1: Server (Kharej)](#step-1-setup-server-kharej--vpn-server)
  * [Step 2: Client (Iran)](#step-2-setup-server-iran--cliententry-point)
* [Advanced Configuration (KCP Modes)](#advanced-configuration-kcp-modes)
* [Network Optimization](#network-optimization-optional)
* [Included Tools](#included-tools)
* [Troubleshooting](#troubleshooting-paqet-installation-issues)
* [Need Help](#%EF%B8%8F-need-help)
* [Requirements](#requirements)
* [Screenshots](#-script-screenshots)
* [License](#license)
* [Credits](#credits)

---

## What's Improved / Optimizations

In this fork (ahmadmute) the following improvements were made:

| Area | Change |
|------|--------|
| **Port handling** | All ports (listen, server, forward, V2Ray) are **trimmed** (spaces/tabs removed) and **validated** (1–65535). Prevents broken configs when a port is entered with spaces or invalid values. |
| **Config reliability** | Ports written to YAML are always clean numbers, so server and client connect correctly and iptables rules use the right port. |
| **UI / Banner** | Redesigned banner with clearer layout, colors (cyan/green/yellow), and credits. Main menu has separators and consistent spacing. |
| **Credits** | Script and README clearly credit: **Paqet** (hanselime), **Manager idea** (behzadea12), **This fork** (ahmadmute). |
| **Port list** | Forward/V2Ray port lists (e.g. `9090, 9091`) are normalized: extra commas and spaces removed before use. |

---

## Installation Steps

### Step 1: Setup Server (Kharej – VPN Server)

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/ahmadmute/Paqet-Tunnel-Manager/main/paqet-manager.sh)
```

1. **Option 2** (Kharej)
2. Custom name for the tunnel
3. Press Enter *(auto)* for interface, local IP, gateway MAC
4. **Listen port** (e.g. `555`)
5. Save the **secret key**, press **Y**
6. KCP: option 1 (or custom), conn value, MTU (e.g. 1350)
7. **Option 2**, then V2Ray/OpenVPN port(s): single `555` or multiple `555,666,777`

---

### Step 2: Setup Server (Iran – Client/Entry Point)

1. **Option 3** (Iran)
2. Kharej server **IP**
3. Same **port** as Kharej (e.g. `555`)
4. **Secret key** from Kharej
5. Custom name, then Enter for auto fields
6. KCP settings (same as Kharej)
7. Forward ports: `555` or `555,666,777`

---

## Advanced Configuration (KCP Modes)

| Mode    | Speed   | Latency | Resources |
|--------|--------|---------|-----------|
| normal | Normal | Normal  | Low       |
| **fast** | Balanced | Low   | Normal *(recommended)* |
| fast2  | High   | Lower   | Moderate  |
| fast3  | Max    | Very low| High      |
| manual | Custom | Custom  | Custom    |

---

## Network Optimization (Optional)

Run the script → **Option 7**:

1. **BBR** – TCP congestion *(Kharej)*
2. **DNS Finder** – Best DNS for Iran *(Iran)*
3. **Mirror Selector** – Fastest APT mirror *(Iran)*

---

## Included Tools

* [BBR (across)](https://github.com/teddysun/across/) – TCP congestion control
* [IranDNSFinder](https://github.com/alinezamifar/IranDNSFinder) – DNS for Iran
* [DetectUbuntuMirror](https://github.com/alinezamifar/DetectUbuntuMirror) – APT mirror (Ubuntu/Debian)

---

## Troubleshooting: Paqet Installation Issues

If Paqet fails to install:

1. Download manually: [hanselime/paqet releases](https://github.com/hanselime/paqet/releases)  
   Use `paqet-linux-amd64-*.tar.gz` (x86_64) or `paqet-linux-arm64-*.tar.gz` (arm64).
2. Put the file in: `/root/paqet/`  
   `mkdir -p /root/paqet`
3. Run the manager again – it will detect and install from that folder.

---

## ⚠️ Need Help?

* **This fork:** [ahmadmute](https://github.com/ahmadmute)
* **Original manager:** [@behzad_developer](https://t.me/behzad_developer) (behzadea12)

---

## Requirements

* Linux (Ubuntu, Debian, CentOS, etc.)
* Root access
* `libpcap-dev`, `iptables`, `paqet`

---

## 📸 Script Screenshots

<details>
<summary>Main Menu</summary>
<br>
<img src="images/Main_Menu.png" width="800">
</details>

<details>
<summary>Install Paqet</summary>
<br>
<img src="images/Install_paqet.png" width="800">
</details>

<details>
<summary>List Services</summary>
<br>
<img src="images/List_Services.png" width="800">
</details>

<details>
<summary>Manage Service</summary>
<br>
<img src="images/Manage_Service.png" width="800">
</details>

<details>
<summary>Optimize Server</summary>
<br>
<img src="images/Optimize_Server.png" width="800">
</details>

---

## License

**MIT License**

---

## Credits

| Project / Person | Role |
|------------------|------|
| [hanselime/paqet](https://github.com/hanselime/paqet) | Raw packet tunnel (Paqet) |
| [behzadea12](https://github.com/behzadea12) | Original Paqet-Tunnel-Manager idea & design |
| [ahmadmute](https://github.com/ahmadmute) | This fork – maintained |

---

## 💖 Support

Using this and want to support? The original project accepts:

* **Tron (TRC20):** `TFYnorJt5gvejLwR8XQdjep1krS9Zw8pz3`

Any contribution helps. 🙏
