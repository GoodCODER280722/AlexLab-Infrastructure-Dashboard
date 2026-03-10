# AlexLab Infrastructure Dashboard

A self-hosted infrastructure dashboard and status page for my Docker homelab environment.

This project provides a clean public landing page displaying real-time service health pulled directly from the **Uptime Kuma API**, alongside quick access to internal services running behind **Nginx Proxy Manager**.

The goal of this project was to build a simple but production-style monitoring surface for my lab while learning how to integrate service monitoring APIs into a custom UI.

---

## Overview

The dashboard displays live service status for core infrastructure components:

- AdGuard Home (network DNS filtering)
- Nginx Proxy Manager (reverse proxy & TLS termination)
- Portainer (container management)
- Uptime Kuma (monitoring & uptime checks)
- WebTest service
- Landing page host

Service health is pulled from the **Uptime Kuma Status Page API** and rendered dynamically in the UI.

---

## Architecture

Internet
│
DuckDNS
│
Router (port forwarding 80/443)
│
Nginx Proxy Manager
│
Docker services
├─ AdGuard Home
├─ Portainer
├─ WebTest
└─ Uptime Kuma
│
Status Page API
│
---

## Tech Stack

**Infrastructure**

- Docker
- Docker Compose
- Linux Mint Server (SSH managed)
- Nginx Proxy Manager
- DuckDNS dynamic DNS

**Monitoring**

- Uptime Kuma
- Kuma Status Page API

**Frontend**

- HTML
- CSS
- Vanilla JavaScript
- Fetch API

---

## Features

- Real-time service health indicators
- Dynamic status updates via Kuma API
- Reverse proxy routing through Nginx Proxy Manager
- TLS automation using Let's Encrypt
- Public dashboard with minimal attack surface
- Self-hosted monitoring stack

---

## Example Dashboard Status

Services are displayed with live indicators:
● Online
● Offline
● Unknown


The dashboard polls the Kuma API every 30 seconds and updates service health automatically.

---

## Example Script

The dashboard fetches monitor metadata and heartbeat status from Kuma and maps them to UI elements.

```javascript
const META="/api/status-page/alexlab";
const HEART="/api/status-page/heartbeat/alexlab";

function normalize(name){
  return name.toLowerCase().replace(/[^a-z0-9]/g,"");
}

---
Why I Built This

This project was created to:

Learn how monitoring APIs work

Practice integrating infrastructure services with a custom UI

Build a real monitoring surface for my homelab environment

Gain experience troubleshooting API responses and service routing


Future Improvements

Planned improvements include:

latency metrics display

uptime percentage tracking

service response times

Grafana integration

dark/light theme toggle

alerting hooks


Author

Alex Crick

Self-hosted infrastructure enthusiast exploring container orchestration, monitoring, and AI-assisted development.

Portfolio:
(https://alex-crick-ai-portfolio.notion.site/Alex-Crick-AI-Prompt-Engineering-Portfolio-2f06340f43dc80388661dfdd8b1b066a)
