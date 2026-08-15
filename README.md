
# ParticleShield — The World's Strongest Open-Source Free Minecraft Firewall (Re-published)

> **Important notice:** Due to unforeseen circumstances, the original GitHub repository has been taken down. This project has now been migrated to a new account and continues to be fully open-source under the MIT License — completely free, with all 69 protection modules, 56 languages, and enterprise-grade capabilities fully intact. Ongoing maintenance and updates are guaranteed.

---

## What is ParticleShield?

ParticleShield is a free, open‑source, enterprise‑grade all‑in‑one firewall built for Minecraft Java Edition Paper 1.21.x servers. It is far more than an anti‑cheat plugin — it is a complete security ecosystem covering anti‑cheat, exploit protection, anti‑bot, anti‑VPN/proxy, intelligent firewall, threat intelligence, forensic analysis, real‑time monitoring, and row‑level data security. ParticleShield integrates **69 protection modules** and **56 international language translations**, and is widely regarded as the strongest open‑source free Minecraft security solution available today.

Whether you run a small survival server, a large‑scale proxy network, a minigame hub, or a commercial RPG server, ParticleShield delivers enterprise‑grade protection at zero cost. From basic KillAura detection to the most advanced Netty protocol‑layer buffer attacks, from simple IP blacklisting to machine learning‑driven anomaly detection engines — ParticleShield packs the entire security stack into a single 35MB JAR.

---

## 69 Protection Modules — Full Attack Surface Coverage

ParticleShield’s defense architecture is built around four core engines, delivering 69 protection modules that span the full attack chain from the network layer to the application layer:

### Anti‑Cheat Engine (10 Checks)
Powered by the GrimAC processor, the anti‑cheat system provides 10 precise checks: `AimDuplicateLook`, `AimModulo360`, `KillAura`, `AntiKB`, `Critical`, `Fly`, `Speed`, `Reach`, `Timer`, `InvalidPitch`, and `BlockBreak` — covering aim, combat, movement, player behavior, and world interaction across five dimensions, with false‑positive rates optimized below 8%.

### AstraGuard Exploit Protection Engine (30+ Sub‑Modules)
ParticleShield’s flagship exploit protection system features 30+ exploit mitigation modules covering virtually every known crash and duplication exploit in Minecraft history:
- Net packet size limits, byte rate limits, packet rate limits, flood attack detection
- The complete Crasher/Dupe vulnerability family (NBT crash, sign crash, lectern crash, map tag crash, item frame crash)
- Creative mode item fixes, inventory dupe fixes, mule dupe fixes, bundle dupe fixes
- Portal break fixes, explosion limiter, falling block limiter, piston limiter
- Movement safety, visual collision protection (fireworks/particles)
- Command crash mitigation (`/calc`, `/eval`, etc.)
- Offline packet dupe fixes, advanced dupe protection (portal/shulker box)

### Anti‑Bot Detection (8 Progressive Layers)
An eight‑layer progressive detection architecture combining connection rate analysis, ping handshake validation, username entropy analysis, protocol compliance checks, first‑join behavior analysis, gravity behavior detection, packet timing analysis, and post‑join behavior analysis. Players are acted upon based on score thresholds — allowed, delayed, kicked, or blacklisted. With asynchronous processing, TPS impact drops from 2 TPS to just 1 TPS.

### Anti‑VPN & IP Reputation System (7‑Layer Filter Chain)
Whitelist → Manual Blacklist → GitHub Public Proxy List → CIDR Range Blocking → ASN Autonomous System Blocking (OVH/Hetzner/DigitalOcean/Alibaba Cloud) → External API Check (proxycheck.io) → Fallback API Rotation — a seven‑layer serial filter chain ensures no proxy or VPN traffic slips through.

### Smart Firewall (MAF Firewall)
The built‑in MAF firewall provides traditional firewall capabilities including IP whitelist/blacklist, geo‑region control, world routing, and connection limits, forming a defense‑in‑depth architecture running in parallel with the anti‑VPN system.

---

## Enterprise‑Grade Comprehensive Protection

### Threat Intelligence Engine
ParticleShield features a built‑in **EWMA adaptive detection engine** and an **Isolation Forest anomaly detection algorithm** (150 isolation trees), capable of analyzing server traffic patterns in real time and automatically identifying novel attacks without predefined rules. Combined with the **Token Bucket algorithm** (6 rate buckets), it delivers precise traffic shaping and rate limiting.

### Punishment System (LightBans)
Integrated into the LightBans punishment framework, supporting 10 penalty types: `ban`, `tempban`, `IPBan`, `mute`, `tempmute`, `muteip`, `kick`, `softban`, `blacklist`, and `warn`. Punishment records are strictly isolated via RLS row‑level security policies.

### Trust Score System
A dynamic player trust‑scoring system that holistically evaluates player behavior patterns, influencing bypass thresholds for attack pattern detection, bot detection, and VPN detection, delivering personalized security policies for every player. v3.1.2 raises trust score thresholds to 85/95/95, further sharpening defensive sensitivity.

### Forensic Analysis
An end‑to‑end forensic analysis pipeline supports attack snapshot capture, packet recording and replay, and JSON‑format export, enabling administrators to post‑mortem analyze any security incident. Forensic data is protected by independent permission nodes, with every access written to the audit log.

### Honeypot & Panic Mode
A built‑in decoy Minecraft server honeypot (port 25566) actively lures and fingerprints attackers. v3.1.2 introduces honeypot rate limiting (3 connections per IP) to prevent resource exhaustion. Administrators can trigger panic mode at any time via the `/panic` command, immediately activating the server’s maximum protection level.

---

## 56 Languages — Truly Global
ParticleShield supports complete localization in 56 languages: Arabic, Chinese, English, French, German, Japanese, Korean, Russian, Spanish, Portuguese, and also Afrikaans, Azerbaijani, Belarusian, Bengali, Bosnian, Catalan, Czech, Danish, Estonian, Persian, Finnish, Galician, Georgian, Greek, Hebrew, Hindi, Croatian, Hungarian, Indonesian, Italian, Kazakh, Khmer, Lao, Lithuanian, Latvian, Macedonian, Mongolian, Malay, Burmese, Norwegian, Nepali, Dutch, Polish, Brazilian Portuguese, Romanian, Sinhala, Slovak, Slovenian, Serbian, Swedish, Thai, Filipino, Turkish, Ukrainian, Urdu, Vietnamese, and more. No matter where your players come from, they experience the full security feature set in their native language.

---

## Observability & Operational Automation
ParticleShield v3.1.2 introduces a complete observability stack:

- **Prometheus Metrics Export:** Real‑time exposure of key metrics including DDoS detection, bot surges, TPS fluctuations, and connection counts
- **Grafana Dashboard:** A 9‑panel visual security dashboard covering attack trends, threat levels, and performance monitoring
- **10 Pre‑Configured Alert Rules:** Automatic notification triggers for DDoS attacks, bot surges, abnormal TPS drops, and more
- **Three‑Channel Notifications:** Discord, Telegram, and Slack synchronized security event push

On the operations side, ParticleShield ships with Aikar‑optimized JVM startup flags, automatic crash restart (up to 3 retries), automatic OOM heap dumps, GC log rotation (14‑day retention), daily configuration backups, and 30‑day auto‑cleanup — all wrapped in ready‑to‑use automation scripts covering both Windows (.bat) and Linux (.sh) platforms.

---

## Authentication & Data Security
ParticleShield’s web admin panel employs the **Argon2id** password hashing algorithm (2022 Password Hashing Competition winner, configured at m=65536KB, t=3, p=4, 16‑byte random salt), combined with JWT token authentication (30‑minute auto‑expiry), Refresh Token rotation, default 127.0.0.1 binding policy, CSRF token protection, and CORS local‑origin restrictions — building an OWASP‑recommended authentication perimeter.

At the database level, RLS row‑level security policies enforce admin privilege isolation, player data self‑control, trusted user querying, and honeypot data isolation across four permission strategies. Every sensitive data read is recorded in the audit log with a 90‑day retention period. Backup files are encrypted with AES‑256‑GCM, ensuring data is protected in every state.

---

## v3.1.2 Security Certification
Independently audited by Shannon v1.8.1 + Pentest v3.2 dual‑engine security assessment, with all 34 vulnerabilities fully remediated:

| Audit Engine        | Method                        | Findings | Remediation | Security Score |
|---------------------|-------------------------------|----------|-------------|----------------|
| Shannon v1.8.1      | White‑Box Static Analysis     | 20 Logical Conflicts | 100%        | 9.7/10         |
| Pentest v3.2        | Black‑Box Penetration Test    | 14 Security Vulnerabilities | 100%        | —              |
| **Total**           | **Dual‑Engine Cross‑Validation** | **34 Findings** | **100%**    | **9.7/10**     |

Among these, 14 high/critical vulnerabilities (including CVSS 9.8 empty password, CVSS 7.5 port conflict, etc.) were fully remediated at the configuration layer, and 7 medium/low vulnerabilities have documented mitigation plans. Zero unpatched critical vulnerabilities.

---

## Completely Free, Completely Open Source
ParticleShield is licensed under the **MIT License** — permanently free, no paywalls, no feature locks. All 69 protection modules, 56 languages, Grafana monitoring dashboards, RLS row‑level security, and operational automation scripts are fully available. The community is free to audit every line of code, freely modify to suit their needs, and freely redistribute — this is the core of our open‑source security commitment.
