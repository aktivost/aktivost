# 🛡️ Aktivost

Aktivost is an open-source, censorship-resistant media platform for activists, journalists, and whistleblowers. It provides a secure and anonymous system for sharing sensitive media over Tor, with public visibility via a clearnet PWA. Designed for maximum privacy, extensibility, and modular deployment — Aktivost empowers users to resist surveillance, censorship, and data exploitation.

---

## 🔍 Core Features

- Anonymous uploads via Tor (.onion gateway)
- WASM-based Proof-of-Work challenge (JS-optional)
- Full metadata stripping (images, video, documents, audio)
- Redis queue for moderation, processing, and archiving
- PostgreSQL or SQLite with encrypted metadata
- Role-based dashboards for Admin, Moderator, Tech
- Plugin system with secure signature checks and hot-reload
- Public PWA viewer (.org) with responsive layout, tile view, search/filter
- File encryption, auto-expiry, and backup to external locations
- Admin panel supports SaaS mode, white-label branding, domain mapping

---

## 🌐 Frontends

| Channel        | Purpose                                  | Stack                     |
|----------------|-------------------------------------------|---------------------------|
| `.onion` site  | Uploads, admin panel, donation panel      | Flask, Tailwind, PoW/WASM |
| `.org` site    | Clearnet public viewer (read-only)        | PWA, Tailwind, no JS req. |

---

## 🔐 Security

- No logging, cookies, or tracking
- PoW throttling against bots
- Secure PGP-based login (simulated or enforced)
- Self-signed SSL in dev, Let's Encrypt for prod
- Modular encryption and metadata scrub
- File archiving + encrypted backup (S3, FTP, IPFS)

---

## 📦 Plugin Architecture

- Signed ZIP upload via admin panel
- Auto-discovered with plugin manifest (`plugin.json`)
- Plugins can register routes, templates, tasks, CLI commands
- Can extend moderation, scrub, or viewer logic
- PGP-signed, loaded into isolated sandbox

---

## 🔌 Plugin Catalog

| Plugin Name               | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| `clamav_scanner`          | Virus/malware scan on uploads                                               |
| `video_live_plugin`       | Anonymous video livestream + viewer chat                                    |
| `wallet_giftcard_plugin`  | Convert gift cards to Monero for donations                                  |
| `monero_wallet_plugin`    | Display XMR wallet QR + address for .onion donations                        |
| `cold_storage_trigger`    | Auto-archive expired files to FTP/S3/IPFS                                   |
| `access_log_analyzer`     | Analyze and visualize access logs (locally only)                            |
| `manual_restore`          | Admin plugin to browse and restore files from cold storage                  |
| `vpn_detector_plugin`     | Advises users if no VPN is detected on upload                               |
| `audio_video_scrambler`   | Obfuscate voice or video identity on media files                            |
| `document_pdf_merger`     | Merge scanned image uploads into secure PDFs                                |
| `tenant_auto_deploy`      | Auto-deploy SaaS tenants based on region and cause                          |
| `stats_dashboard_plugin`  | Display platform activity (mod-only)                                        |
| `pgp_identity_plugin`     | Upload, verify, and assign mod/admin keys with fingerprint match            |

---

## 🛠️ Stack

- **Flask** + Blueprints
- **Tailwind CSS** (PWA, responsive, dashboard UI)
- **Redis** + Worker Queues
- **PostgreSQL / SQLite**
- **MinIO**, S3-compatible FS, or FTP
- **Docker** + **Nomad** job orchestration
- **GnuPG**, **ClamAV**, **WASM**

---

## 📜 License

Licensed under **Creative Commons BY-NC-ND 4.0**.  
No commercial use. No warranty. Plugins are modular and may carry additional restrictions.

> ⚠️ Use responsibly. This software is intended to protect life and privacy — not for illegal or unethical purposes.

---

## 🤝 Want to Contribute?

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines, plugin builder help, and security best practices.

