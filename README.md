# Zeshan Nasir

**System Administrator at Optimizely · Stockholm, Sweden**  
Leading Atlassian AI, workflow automation, and documentation governance across Jira, JSM, and Confluence Cloud.

---

### Open Work

- **[ai-local](https://github.com/ZeshanNasir/ai-local)** — Empirical Apple Silicon benchmark harness and local AI control plane (M4 Pro / Metal).

---

### Two compute planes

Routine engineering work runs locally and cuts recurring token bills. Runtimes bind to loopback only; network egress is audited separately.

#### Workstation · MacBook Pro M4 Pro, 48 GB

| Metric | Specification |
| :--- | :--- |
| **Runtime** | Ollama (MLX) · `flint:40b` · `nemotron:e4b` |
| **Job** | Interactive engineering: code audit, subagent loops |
| **Measured** | 100/100 Tier S · 1,176–1,776 tok/s prefill · 82–105 tok/s decode · 22 GB weights in RAM, zero swap |

#### Continuous ops · Minisforum MS-02 Ultra (Core Ultra 5, 6 P-cores)

| Metric | Specification |
| :--- | :--- |
| **Runtime** | `ik_llama.cpp` (AVX-VNNI) · `Ling-3.0-tiny` (MoE) |
| **Job** | 24/7 services: MCP tool-calling, n8n triage, Home Assistant |
| **Measured** | 0.176 s TTFT · 511 tok/s prefill · 39.8 tok/s decode · 131K context in ~7.1 GiB RAM · ~20 W wall power |

> **Cost model:** A workstation amortized at about $75–$80 per seat per month over 4 years replaces variable token bills with $0.00 marginal cost per token for routine developer loops.

---

### Systems & Platforms

`Atlassian Cloud (Jira / JSM / Confluence / Rovo)` · `Microsoft Entra ID` · `Microsoft Intune` · `Jamf Pro` · `Apple Silicon Metal (MLX)` · `Linux / Proxmox VE`

---

[Website & Architecture Record ↗](https://zeshannasir.com) &nbsp;·&nbsp; [LinkedIn ↗](https://linkedin.com/in/zeshan-nasir) &nbsp;·&nbsp; [Email ↗](mailto:contact@zeshannasir.com)
