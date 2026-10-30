# Zeshan Nasir

**System Administrator at Optimizely · Stockholm, Sweden**  
Leading Atlassian AI, workflow automation, and documentation governance across Jira, JSM, and Confluence Cloud.

---

### Open Work

- **[ai-local](https://github.com/ZeshanNasir/ai-local)** — Empirical Apple Silicon benchmark harness and local AI control plane (M4 Pro / Metal). Evaluates throughput, memory saturation, and cost/privacy trade-offs for running engineering tasks on-device under a strict One-Hot VRAM policy.

---

### Compute Tiering & Local Inference Architecture

Frontier cloud models excel at unbounded system design, but routing high-volume routine tasks (incident logs, document indexing, code triage) to metered APIs introduces recurring token costs and data egress risk.

I design and measure zero-egress, hardware-aligned inference across two dedicated physical tiers:

#### 1. Workstation Tier — Apple Silicon M4 Pro (48 GB Unified Memory)
Evaluated via **[ai-local](https://github.com/ZeshanNasir/ai-local)**. Native Ollama MLX runtime with zero proxy daemons. Binds directly to terminal engineering tools (`opencode`, `claude`) with on-the-fly model switching (`/model`). Strict One-Hot VRAM policy (zero swap spillover).

- **Deep Reasoning & Code Audit:** `flint:40b` (39.8B MoE, ~2.5B active parameters). 90–105 tok/s decode, 1,176–1,776 tok/s prefill, 100/100 score on Tier S engineering torture test.
- **Subagent Loops & Triage:** `nemotron-3.5-bolt:e4b` (105–123 tok/s decode, 510 tok/s prefill).
- **Multimodal & Vision:** `gemma4:26b-mlx` (70+ tok/s) and `qwen3.6:35b-mlx` (72–85 tok/s).
- **Sustained Context Defense:** Quantized 8-bit KV buffers (`q8_0`) halve cache footprint, sustaining 64K–100K token sessions in unified RAM without swap.

#### 2. Continuous Operations Tier — Minisforum MS-02 Ultra (~20W Wall Power)
Headless background inference running 24/7 on an Intel Core Ultra 5 pinned to 6 physical Performance cores (`cpuset 0-5`). Idles at ~8.5–9.5W CPU package power (~20–23W total wall draw) at ~43°C.

- **The Bandwidth Solution:** Deployed upstream `ik_llama.cpp` with AVX-VNNI acceleration, Flash Attention (`-fa on`), and asymmetric quantized caching (`q8_0` keys / `q4_0` values).
- **Operational Reality:** `Ling-3.0-tiny` (7.89B MoE, ~1.3B active parameters). Holds a complete 131,072 context window in **7.48 GB total RAM**. Sustains **39.8 tok/s decode**, **511 tok/s prefill**, and sub-0.2s TTFT on CPU.
- **Active Workloads:** Serves frontline Model Context Protocol (MCP) tool-calling, n8n workflow triage, Home Assistant natural language intents, and deterministic schema audits (`[OBSERVED]`, `[INTERPRETED]`, `[UNKNOWN]`).

#### Enterprise Economics & Data Residency
- **Fixed CapEx vs. Metered OpEx:** Standard enterprise laptop procurement (approx. $3,500–$4,000 USD / 48 GB unified RAM SKU) amortizes to **approx. $75–$80/month per seat** over a 4-year corporate refresh cycle—replacing volatile cloud token bills with $0.00 marginal cost per token.
- **Strict Data Residency:** Binds strictly to loopback (`127.0.0.1`). Enables automated contract review, HR policy verification, and sensitive infrastructure log triage with zero risk of corporate IP leakage or external provider training.

---

### Systems & Platforms

`Atlassian Cloud (Jira / JSM / Confluence / Rovo)` · `Microsoft Entra ID` · `Microsoft Intune` · `Jamf Pro` · `Apple Silicon Metal (MLX)` · `Linux / Proxmox VE`

---

[Website & Architecture Record ↗](https://zeshannasir.com) &nbsp;·&nbsp; [LinkedIn ↗](https://linkedin.com/in/zeshan-nasir) &nbsp;·&nbsp; [Email ↗](mailto:contact@zeshannasir.com)
