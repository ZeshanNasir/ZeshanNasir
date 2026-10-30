# Zeshan Nasir

**System Administrator at Optimizely · Stockholm, Sweden**  
Leading enterprise identity, documentation governance, and AI-assisted workflows across Atlassian Cloud (Jira, JSM, Confluence, Rovo, Risotto), Microsoft Entra ID, Intune, and Jamf Pro.

---

### Local AI & Empirical Inference

Frontier cloud models excel at high-uncertainty system design, but routing repetitive, high-volume, or sensitive workloads (log triage, code review, AST diffs, internal automation) to paid APIs introduces unnecessary recurring token costs and data egress risk.

I design and measure zero-egress, hardware-aligned local inference architectures across two distinct physical planes:

#### 1. Workstation Plane — Apple Silicon (M4 Pro 48 GB Unified Memory)
Evaluated via **[ai-local](https://github.com/ZeshanNasir/ai-local)**. Native Ollama MLX runtime with zero proxy daemons or custom wrappers. Directly binds to standard engineering tools (`opencode`, `claude`) with on-the-fly model switching (`/model`). Strict One-Hot VRAM policy (zero swap spillover).

- **Deep Reasoning & Code Audit:** `flint:40b-a2b-qat-int4` (39.8B MoE, ~2.5B active parameters). 90–105 tok/s decode, 1,176–1,776 tok/s prefill, 100/100 score on Tier S engineering torture test.
- **Subagent Loops & Triage:** `nemotron-3.5-bolt:e4b`. 105–123 tok/s decode, 510 tok/s prefill.
- **Multimodal & Vision:** `gemma4:26b-mlx` (70+ tok/s) and `qwen3.6:35b-mlx` (72–85 tok/s).
- **Dense Embeddings & Policy Gates:** `embeddinggemma-2:740m` (<1.5 GB VRAM) and `tev1:4b-mxfp8` (single-forward decision classification).

#### 2. Infrastructure Plane — Intel Core Ultra CPU (MS02 Homelab / 23W Wall Power)
Continuous deterministic background operations without a 300W dedicated GPU rig. Runs on an Intel Core Ultra 5 235HX pinned to 6 physical Performance cores (`cpuset 0-5`). Idles at ~8.5–9.5W CPU package power (~20–23W total wall draw) at ~43°C.

- **The Bandwidth Bottleneck:** Standard CPU inference engines choke on high-context FP16 KV-caches, causing severe memory bandwidth starvation.
- **The Upstream Solution:** Deployed Iwan Kawrakow's upstream `ik_llama.cpp` fork with AVX-VNNI acceleration, Flash Attention (`-fa on`), and asymmetric quantized caching (`q8_0` keys / `q4_0` values).
- **Inference Profile:** `Ling-3.0-tiny` (7.89B MoE, ~1.3B active parameters). Entire 131,072 context window compressed into **7.48 GB total RAM**. Sustains **39.8 tok/s decode** and 511 tok/s prefill with sub-0.2s TTFT on CPU.

---

### Open Work

- **[ai-local](https://github.com/ZeshanNasir/ai-local)** — Empirical Apple Silicon benchmark harness and local AI control plane (M4 Pro / Metal). Reproducible throughput, memory saturation, and model evaluation under a strict One-Hot VRAM policy.

---

### Systems & Platforms

`Atlassian Cloud (Jira / JSM / Confluence)` · `Atlassian Rovo & Risotto` · `Microsoft Entra ID` · `Microsoft Intune` · `Jamf Pro` · `Apple Silicon Metal (MLX)` · `Linux / Proxmox VE`

---

[Website & Architecture Record ↗](https://zeshannasir.com) &nbsp;·&nbsp; [LinkedIn ↗](https://linkedin.com/in/zeshan-nasir) &nbsp;·&nbsp; [Email ↗](mailto:contact@zeshannasir.com)
