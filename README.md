# Zeshan Nasir

> **System Administrator · Atlassian AI & Automation · Stockholm, Sweden**  
> *Structuring operational knowledge lifecycles, sandbox-testing service workflows, and ensuring enterprise AI assistants retrieve verified ground truth.*

---

### 🔬 Featured Open Project

### [ai-local](https://github.com/ZeshanNasir/ai-local)
**Empirical Local AI Engineering & Benchmark Harness for Apple Silicon**

Deterministic, reproducible evaluation of quantized open-weight models on Apple Silicon (M4 Pro / Metal). Measures decode throughput, task completion, and memory pressure under real runtime constraints.

| Model | Format | Decode Speed | Synthetic Tasks | Real Hardware Finding |
| :--- | :--- | :---: | :---: | :--- |
| **`qwen3.6:35b-mlx`** | 36B MoE (nvfp4) | **68 tok/s** | 43/45 | High interactive throughput; fast prompt evaluation. |
| **`gemma4:26b-mlx`** | 26.2B MoE (nvfp4) | **60 tok/s** | 42/45 | Fast generation; multi-turn agent execution resolves code fixes. |
| **`qwen3.8:27b-mlx`** | 27.8B Dense (nvfp4) | **26 tok/s** | 42/45 | Dense specialist; bandwidth-bound decode speed. |

> *Reference: Apple M4 Pro (48 GB), macOS, Ollama, 8,192 context window. See [`RESULTS.md`](https://github.com/ZeshanNasir/ai-local/blob/main/RESULTS.md) for raw runs.*

---

### 🛠️ Systems & Technical Architecture

| Domain | Systems & Tooling | Focus & Operational Reality |
| :--- | :--- | :--- |
| **Atlassian AI & Governance** | Confluence Cloud · JSM · Jira · Atlassian Rovo · Risotto | Documentation lifecycles, automated obsolete quarantine, Tier-0 self-service deflection & approval boundaries. |
| **Identity & Fleet Operations** | Microsoft Entra ID · Okta · Microsoft Intune · Jamf Pro | Enterprise identity & access workflows, macOS and Windows fleet configurations, hardware inventory & Service Desk escalations. |
| **Local AI Inference (`ai-local`)** | Apple Silicon M4 Pro (48GB) · Ollama MLX · Metal | One-Hot VRAM fleet: **Qwen** (`qwen3.6:35b-mlx`, 256K) for systems reasoning; **Gemma** (`gemma4:26b-mlx`, 256K) for vision & intake. |
| **Private Infrastructure Lab** | Linux · Proxmox VE · WireGuard · PBS | Two-node hypervisor cluster, service isolation, network egress auditing & empirical backup restore testing. |

---

### ⚙️ Operating Principles

- **Ground Truth Over Generation:** Confluence remains the authoritative source of truth. AI assistants consume verified knowledge; they do not replace its authority.
- **Ticketed Change & Sandbox Gates:** Every system modification is ticket-driven, audited, and validated in sandbox environments prior to production rollout.
- **Separation of Concerns:** Employer systems (Optimizely) and personal empirical engineering labs (`ai-local`) remain strictly separated.
- **No Privacy Claims Without Egress Proof:** Distinguish local execution from network isolation. Make no privacy claim without an empirical traffic capture.

---

### 🌐 Canonical Record & Contact

- **Authoritative Portfolio & Case Studies:** [zeshannasir.com](https://zeshannasir.com)
- **LinkedIn Profile:** [linkedin.com/in/zeshan-nasir](https://linkedin.com/in/zeshan-nasir)
- **Direct Contact:** [contact@zeshannasir.com](mailto:contact@zeshannasir.com)
