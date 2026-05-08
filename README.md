# Snipe-IT Asset Management Lab

A self-hosted IT asset management system deployed on Oracle Cloud Infrastructure (OCI), simulating a real-world 10-person company environment called **Trev Technologies**. Built as a portfolio project to demonstrate practical IT help desk and systems administration skills.

---

## 🛠️ Tech Stack

- **Snipe-IT** v8.5.0 — open-source IT asset management
- **Ubuntu 24.04** on Oracle Cloud Infrastructure (Always Free tier)
- **Nginx** — web server
- **MariaDB** — database backend
- **PHP 8.2** — application runtime
- **WireGuard VPN** — also running on the same OCI instance (see [wireguard-oci-vpn](https://github.com/trevjacq/wireguard-oci-vpn))

---

## 🎯 Project Goals

- Deploy and configure a production-grade ITAM system from scratch on a Linux cloud server
- Simulate a realistic IT inventory environment for a small business
- Practice asset lifecycle management, user provisioning, and license tracking
- Demonstrate multi-service Linux server administration (Snipe-IT + WireGuard on one instance)

---

## 🏢 Mock Environment — Trev Technologies

The lab environment simulates a 10-person company with the following inventory:

| Category | Count |
|---|---|
| Laptops | 5 |
| Desktops | 3 |
| Monitors | 4 |
| Networking Equipment | 3 |
| Accessories | 3 |
| Software Licenses | 4 |
| **Total Assets** | **18** |

### Users
Five mock employees across different departments and locations (Main Office and Remote):

| Name | Title | Location |
|---|---|---|
| Sarah Johnson | Marketing Manager | Main Office |
| Marcus Williams | Software Engineer | Main Office |
| Priya Patel | Product Manager | Remote |
| James Carter | Sales Representative | Main Office |
| Lisa Thompson | Office Administrator | Main Office |

### Software Licenses Tracked
- Microsoft 365 Business Premium (10 seats)
- CrowdStrike Falcon Go (10 seats)
- Zoom Business (10 seats)
- Adobe Acrobat Pro (3 seats)

---

## ⚙️ Deployment Overview

Snipe-IT was deployed on an existing OCI Ubuntu instance alongside a WireGuard VPN server, demonstrating multi-service Linux administration.

**Key deployment steps:**
1. Added Ondrej PHP PPA to access PHP 8.2 on Ubuntu 24.04
2. Installed and secured MariaDB, created dedicated database user
3. Cloned Snipe-IT from GitHub, installed dependencies via Composer
4. Configured `.env` with database credentials and app URL
5. Set up Nginx as reverse proxy with PHP-FPM socket
6. Opened port 80 via OCI Security List and iptables
7. Completed web-based pre-flight configuration check (all green)

---

## 🔐 Security Notes

- Database user `snipeit` has least-privilege access (only the `snipeit` database)
- Nginx configured to deny access to `.htaccess` files
- `.env` file verified as inaccessible from the public web
- OCI instance firewall (iptables) configured alongside cloud-level security lists
- WireGuard VPN running on the same host on UDP 51820 — no port conflicts

---

## 📋 Asset Lifecycle SOP

See [ASSET_SOP.md](./ASSET_SOP.md) for standard operating procedures covering:
- New asset onboarding
- Asset assignment and checkout
- Asset return and check-in
- Asset retirement and disposal

---

## 🔗 Related Projects

- [wireguard-oci-vpn](https://github.com/trevjacq/wireguard-oci-vpn) — WireGuard VPN on OCI (same server)
- [siem-home-lab](https://github.com/trevjacq/siem-home-lab) — Elastic Stack SIEM with MITRE ATT&CK detection rules
- [network-traffic-analyzer](https://github.com/trevjacq/network-traffic-analyzer) — Python/Scapy packet capture tool
- [phishing-email-detector](https://github.com/trevjacq/phishing-email-detector) — ML-based phishing classifier with Claude API

---

## 👤 Author

**Trevor Young**  
IT & Security Operations | CompTIA Security+ (SY0-701)  
[LinkedIn](https://www.linkedin.com/in/trevor-young-) | [Portfolio](https://trevjacq.github.io) | [GitHub](https://github.com/trevjacq)
