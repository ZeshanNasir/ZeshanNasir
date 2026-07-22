```text
┌──────────────────────────────────────────────────────────────────────────┐
│ [SYS_INFO: WHOAMI]                                                       │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│ [NODE_IDENTIFIER] : github.com/ZeshanNasir                               │
│ [CURRENT_ROLE]    : System Administrator @ Optimizely                        │
│ [DEPLOY_REGION]   : Stockholm, SE                                        │
│ [FOCUS]           : Systems Operations, Endpoint Fleets & Automation     │
│ [PRIVATE_LAB]    : Omega (2-Node Proxmox HA, Tailscale Mesh, Local AI)   │
│ [LIVE_DOSSIER]    : https://zeshans.dev                                  │
| [ORCID]           : https://orcid.org/0009-0007-1217-2124          |
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
| `SYSTEM_01: OMEGA_CLUSTER` | Bare-metal Proxmox HA. 2-node cluster + VPS QDevice for split-brain prevention. | Proxmox VE, Corosync, Tailscale mesh, Caddy HTTP/3, daily off-site backup to GDrive. | `NOMINAL` |
| `SYSTEM_02: HERMES_AGENT` | Local-only RAG agent. Telegram interface, vector retrieval, CPU-bound inference. | Qwen 3.6-35B (ik_llama.cpp), Qdrant vector DB, n8n orchestration, asymmetric KV cache (q8_0/q4_0). | `NOMINAL` |
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
    │ CT401 Qwen 3.6-35B     │           │ CT201 ntfy/Miniflux/Memos│
    │ CT402 Qdrant            │           │ CT301 Homepage dashboard │
    │ CT403 n8n/Paperless     │           │ Uptime Kuma · DR store   │
    │ CT404 Grafana           │           │ Daily → Google Drive     │
    │ CT405 PentAGI           │           └──────────────────────────┘
    │ CT406 Hermes            │
    └─────────────────────────┘
```

---

### `[PERFORMANCE_TELEMETRY]`

```text
CT401 Inference · ik_llama.cpp · Measured 2026-06-14

  Decode       ~15 tok/s     RAM-bandwidth ceiling (DDR5-4800, single-socket)
  Prefill      60–167 tok/s  Scales with prompt length and batch size
  TTFT         0.3s short    ~7s at 1171 tokens
  KV Cache     K=q8_0/V=q4_0 Asymmetric quantization, 128K context in 64 GB
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

---

<sub>Last synchronized: 2026-07-18 · Telemetry aligned with <a href="https://zeshans.dev">zeshans.dev</a> and canonical LinkedIn profile.</sub>
