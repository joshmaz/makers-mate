# Advanced Topics: Working Within Lowell Makes (v0.5)

This document captures the internal operations, digital systems, and infrastructure that support Lowell Makes.  
It is intended for titled members, captains, and volunteers who manage systems, documentation, and shop operations.

---

## 1. Organizational Framework

### 1.1 Overview

Lowell Makes operates as a 501(c)(3) nonprofit organization governed by the Board of Directors and the Executive Committee (ExCom).  
The Shop Captains coordinate with ExCom to maintain consistency, safety, and communication.

### 1.2 Leadership and Titled Roles

- **Shop Captains & Co-Captains:** Lead individual shops and maintain cleanliness, tool inventories, and safety standards.  
- **Champions:** Subject-matter experts assisting captains.  
- **Committee Leads:** Education, IT, Safety, Facilities, etc.  
- **ExCom:** Oversees day-to-day governance, finance, and policy.

### 1.3 Cultural Foundations

Lowell Makes fosters collaboration across all its spaces. Each shop supports the success of the collective makerspace.  
Members are expected to act responsibly, communicate transparently, and volunteer time toward shared goals.

---

## 2. Communication and Collaboration Systems

### 2.1 Basecamp

- Primary discussion and project management platform.
- Active Basecamps: Captains, Education, Opportunities, IT, and others.
- Avoid uploading large files directly—link to Google Drive or GitHub instead.

### 2.2 Notion

- Used for structured documentation, project tracking, and membership records.
- Templates for meeting notes, onboarding, and process documentation.
- Links to Basecamp discussions for context.

### 2.3 Google Workspace

- `@lowellmakes.com` accounts for titled members and committees.
- Shared Drives for documents, budgets, and proposals.
- Integrates with Basecamp via shared file links.

### 2.4 GitHub Organization

- Hosts documentation and automation repos.
- Example repos: `lm-shops`, `dakboard-lowellmakes`, `lm-doorflow-sync`.
- Pull request workflow, issue tracking, and markdown standards encouraged.

### 2.5 Email and Mailing Lists

- `excom@lowellmakes.com`, `shopcaptains@lowellmakes.com`, and committee-specific lists.
- Used for formal communication, announcements, and approvals.

---

## 3. Digital Infrastructure and Tech Stack

### 3.1 Network & Connectivity

- **Hardware:** Ubiquiti UniFi switches, access points, and gateways.  
- **Firewall:** pfSense appliance handling VPN, port forwarding, and DNS.  
- **Management:** IT Committee oversees VLANs, Wi-Fi, and DHCP scopes.  
- **Monitoring:** Scheduled firmware updates and planned Grafana integration.

### 3.2 Server Room & Compute

- Rack-mounted servers and UPS systems managed by the IT Committee.
- Hosts automation scripts, signage services, and backups.
- Temperature and power monitored.

### 3.3 Storage Infrastructure

- **Bootmill NAS (File Server):** Mounted as Z: drive on networked computers; shared folders for shops, education, and media assets.  
- **Media Server NAS:** High-throughput array for network-based video editing and production workflows.

### 3.4 Camera Systems

- **Security Cameras:** Ubiquiti Protect Cameras managed by IT and Facilities.  
- **Studio Cameras:** Controlled by the Media Studio; used for photo and video production.

### 3.5 Cloud & Software Services

| Category | Tool | Purpose | Primary Users / Owners |
|-----------|------|----------|------------------------|
| Office Suite | Google Workspace | Email, Docs, Sheets | ExCom + Titled Members |
| Cloud Compute | Google Cloud Platform | Backups, integrations | IT Committee |
| Creative Tools | Canva | Marketing, graphics | ExCom / Marketing |
| Documentation | Notion | Wiki, project tracking | Education / Ops |
| Collaboration | Basecamp | Conversations, tasks | All Members |
| Version Control | GitHub | Documentation, automation | IT / Captains |
| Signage | DAKboard | Shop display boards | IT / Operations |
| Networking | Ubiquiti UniFi | Switches, Wi-Fi, cameras | IT Committee |
| Firewall | pfSense | Routing, VPN | IT Committee |

### 3.6 Planned / Emerging Systems

- Prometheus + Grafana monitoring suite.  
- Automated backup validation and alerting.  
- Unified role-based directory for access management.

---

## 6. Facilities and Safety Systems

### 6.1 Building Layout and Shared Resources

- Overview of floors, shop locations, shared lounges, and signage locations.  
- Physical infrastructure integrated with networked systems (Doorflow, cameras, servers).

### 6.2 Safety Infrastructure

- Fire extinguishers, eyewash stations, and first aid kits.
- Safety Committee manages protocols and quarterly reviews.

### 6.3 Environmental Monitoring

- Sensors for server room temperature, humidity, and power load.  
- Data planned to feed into Grafana dashboards.

### 6.4 Access Control and Automation Infrastructure

#### 6.4.1 Doorflow System

- Centralized fob reader management.  
- Covers front entrance, shop doors, server room, and storage.  
- Administered by IT and Facilities Committees.

#### 6.4.2 Notion ↔ Doorflow Sync Script

- Custom script syncs Notion Team membership with Doorflow access lists.  
- Source: private GitHub repo (`lm-doorflow-sync`).  
- Runs on internal server; executed via cron job.  
- Logs updates and alerts to IT channel.

#### 6.4.3 Member Onboarding Flow

- New member → Added to Notion → Auto-granted shop access via Doorflow.  
- Expired or revoked memberships lose access automatically.

#### 6.4.4 Hardware and Maintenance

- Doorflow controllers connected via PoE on UniFi switches.  
- UPS-backed for power loss continuity.

#### 6.4.5 Future Enhancements

- Integrate sync logs with Grafana.  
- Add Discord/Basecamp notifications.  
- Two-factor admin access for Doorflow portal.

---

## 8. Appendix – Lowell Makes Tech Stack

| Layer | System / Tool | Function | Owner / Committee | Notes |
|-------|----------------|-----------|-------------------|-------|
| Networking | Ubiquiti UniFi | Switches, Wi-Fi, cameras | IT Committee | Managed via UniFi Controller |
| Firewall | pfSense | VPN, DHCP, DNS | IT Committee | VLAN segmentation |
| File Server | Bootmill NAS | Shared folders (Z:) | IT Committee | Backed up locally and to cloud |
| Media Server | NAS #2 | High-speed video editing | Media Studio + IT | 10 GbE link to editing stations |
| Access Control | Doorflow | Fob reader management | IT + Facilities | Syncs with Notion Teams |
| Automation | Doorflow Sync Script | Access automation | IT Committee | Runs on internal server |
| Documentation | Notion | Membership, wiki | Education / Ops | Source of truth for roles |
| Collaboration | Basecamp | Projects & discussions | ExCom / All Members | Core async communication |
| Design | Canva | Marketing graphics | ExCom / Marketing | Shared templates |
| Cloud | Google Workspace | Docs, Sheets, Drive | ExCom / IT | @lowellmakes.com accounts |
| Cloud | Google Cloud Platform | Backups, automation | IT Committee | Under org billing |
| Signage | DAKboard | Shop display boards | IT / Ops | Raspberry Pi endpoints |
| Monitoring (Planned) | Prometheus / Grafana | System metrics | IT Committee | TBD deployment Q1 2026 |

---

_Last updated: October 2025
