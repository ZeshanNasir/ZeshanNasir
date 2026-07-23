```text
┌──────────────────────────────────────────────────────────────────────────┐
│ [SYS_INFO: WHOAMI]                                                       │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│ [NODE_IDENTIFIER] : github.com/ZeshanNasir                               │
│ [CURRENT_ROLE]    : System Administrator @ Optimizely                        │
│ [DEPLOY_REGION]   : Stockholm, SE                                        │
│ [FOCUS]           : Systems Operations, Endpoint Management, Automation  │
│ [PRIVATE_LAB]     : Omega - Proxmox, Tailscale, Infrastructure Experiments│
│ [LIVE_DOSSIER]    : https://zeshans.dev                                  │
│ [ORCID]           : https://orcid.org/0009-0007-1217-2124                │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

**System Administrator** operating enterprise IT systems, endpoint platforms, automation workflows, and private lab infrastructure.
Working one layer below the model, on the data it reads.

---

### `[CORE_THESIS]`

```text
01  AI fails on data before it fails on models.
    └─ A language model asked to answer from outdated, untagged documentation
       will confidently get it wrong. The model is rarely the bottleneck.

02  Knowledge without governance decays.
    └─ Documentation without metadata, expiration, and ownership is a liability
       that compounds. I engineer the lifecycle so the source stays current
       and machine-parseable.

03  Clean inputs, then everything else.
    └─ Confluence governance feeding Workato and ROVO at work. A private RAG
       cluster at home that returns UNKNOWN instead of inventing. Both depend
       on the same thing: a governed, reliable data source.
```

---

### `[INFRASTRUCTURE_NODES]`

| `[Node_ID]` | `[Focus_Domain]` | `[Core_Stack]` | `[System_State]` |
| :--- | :--- | :--- | :--- |
| `SYSTEM_01: OMEGA_CLUSTER` | Bare-metal Proxmox HA. 3-node cluster (hp260, ms02, VPS QDevice). | Proxmox VE, Corosync, Tailscale mesh, Caddy HTTP/3, PBS daily backup. | `NOMINAL` |
| `SYSTEM_02: HERMES_AGENT` | Local-only RAG agent. Telegram interface, vector retrieval, LLM inference. | Qwen 3.6-35B GGUF (Port 8080 API), Qdrant vector DB, n8n orchestration. | `NOMINAL` |
| `SYSTEM_03: KNOWLEDGE_GOVERNANCE` | Confluence lifecycle engineering. Metadata labeling, expiration protocols, machine-parseable sources. | Atlassian ROVO, Workato orchestration bus, automated Jira ticketing, Slack alerting. | `NOMINAL` |

---

### `[CLUSTER_TOPOLOGY]`

```text
                    ┌─────────────────────────────┐
                    │   VPS (QDevice)              │
                    │   Corosync Vote · Caddy Edge │
                    └──────────┬──────────┬────────┘
                   Tailscale   │          │   Tailscale
                      Mesh     │          │      Mesh
              ┌────────────────┘          └────────────────┐
              │                                            │
    ┌─────────▼──────────────┐           ┌─────────────────▼────────┐
    │ ms02                   │ Corosync  │ hp260                    │
    │ Intel Ultra 5 235HX    │◄─────────►│ Intel i5-6200U           │
    │ 64 GB DDR5-4800        │  LINK0    │ 32 GB DDR4               │
    │ Role: AI Inference     │           │ Role: Management / DR    │
    ├────────────────────────┤           ├──────────────────────────┤
    │ CT401 Qwen 3.6-35B GGUF│           │ CT101 Jellyfin / Qdrant  │
    │ CT402 Qdrant            │           │ CT301 Dockge / UniFi     │
    │ CT403 n8n/Paperless     │           │ Uptime Kuma (Port 3310)  │
    │ CT404 Vaultwarden       │           │ PBS VM100 Daily Backup   │
    │ CT405 Security Lab      │           └──────────────────────────┘
    │ CT406 Hermes Agent     │
    └─────────────────────────┘
```

---

### `[PERFORMANCE_TELEMETRY]`

```text
CT401 Inference · Qwen 3.6 35B GGUF · Measured 2026-07-23

  Endpoint     http://192.168.20.21:8080/v1 (OpenAI-Compatible API)
  Context      131,072 Tokens (131K) Context Window
  Decode       ~15 tok/s     RAM-bandwidth ceiling (DDR5-4800, single-socket)
  Prefill      60–167 tok/s  Scales with prompt length and batch size
```

---

### `[CAREER_TIMELINE]`

```text
2012  IT Systems & NOC Support Eng   MicroTech Industries · Lahore
2020  Network & System Admin         Levi Strauss & Co. (via SV Eng) · Lahore
2022  Associate System Admin         Optimizely · Stockholm
2026  System Administrator           Optimizely · Stockholm   ← current
      └─ Focus: Platform Infrastructure, Data Reliability, Zero-Trust Mesh
```

---

### `[TELEMETRY_INGRESS]`

* **Primary Node:** [zeshans.dev](https://zeshans.dev)
* **Professional Dossier:** [LinkedIn Profile](https://www.linkedin.com/in/zeshan-nasir)
* **ORCID Dossier:** [ORCID 0009-0007-1217-2124](https://orcid.org/0009-0007-1217-2124)

---

<sub>Last synchronized: 2026-07-23 · Telemetry aligned with <a href="https://zeshans.dev">zeshans.dev</a> and canonical LinkedIn profile.</sub>
