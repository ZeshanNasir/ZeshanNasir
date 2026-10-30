# Zeshan Nasir

**System Administrator at Optimizely · Stockholm, Sweden**  
Leading Atlassian AI, workflow automation, and documentation governance across Jira, JSM, and Confluence Cloud.

---

### Open Work

- **[ai-local](https://github.com/ZeshanNasir/ai-local)** — Empirical Apple Silicon benchmark harness and local AI control plane (M4 Pro / Metal).

---

### Local AI Architecture & Compute Tiering

Routing routine high-volume engineering tasks locally eliminates recurring cloud token bills and guarantees zero data egress.

| Plane | Hardware & Power | Runtime & Fleet | Purpose & Measured Performance |
| :--- | :--- | :--- | :--- |
| **Workstation** | MacBook Pro M4 Pro<br>`48 GB Unified RAM` | Ollama (MLX)<br>`flint:40b` · `nemotron:e4b` | **Interactive Engineering:** Deep code audit, subagent loops.<br>• 90–105 tok/s decode · 100/100 Tier S benchmark · Zero swap |
| **Continuous Ops** | Minisforum MS-02 Ultra<br>`Intel Core Ultra 5 (6 P-cores)`<br>`~20W wall power` | `ik_llama.cpp` (AVX-VNNI)<br>`Ling-3.0-tiny` (MoE) | **24/7 Autonomous Services:** MCP tools, n8n triage, Home Assistant.<br>• Sub-0.2s TTFT · 511 tok/s prefill · 131K context in 7.5 GB RAM |

> **Enterprise ROI:** Fixed workstation CapEx (approx. $75–$80/month per seat amortized over 4 years) replaces variable cloud token bills with $0.00 marginal cost per token and 100% loopback data residency for sensitive HR, legal, and incident logs.

---

### Systems & Platforms

`Atlassian Cloud (Jira / JSM / Confluence / Rovo)` · `Microsoft Entra ID` · `Microsoft Intune` · `Jamf Pro` · `Apple Silicon Metal (MLX)` · `Linux / Proxmox VE`

---

[Website & Architecture Record ↗](https://zeshannasir.com) &nbsp;·&nbsp; [LinkedIn ↗](https://linkedin.com/in/zeshan-nasir) &nbsp;·&nbsp; [Email ↗](mailto:contact@zeshannasir.com)
