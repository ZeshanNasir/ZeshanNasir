<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=16&duration=2800&pause=900&color=00FF87&center=true&vCenter=true&width=720&lines=System+Administrator+%40+Optimizely;Data+Reliability+for+Automation+and+AI;Confluence+Governance+for+Ticket+Deflection;Measured+Proxmox+and+MLX+Local-RAG+Homelab;Zero-Trust+Tailscale+Mesh)](https://github.com/ZeshanNasir)

</div>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/zeshannasir)
[![Portfolio](https://img.shields.io/badge/Portfolio-zeshannasir.github.io-111?style=flat-square&logo=githubpages&logoColor=white)](https://zeshannasir.github.io)
[![X](https://img.shields.io/badge/X-000?style=flat-square&logo=x&logoColor=white)](https://twitter.com/zeshannasir)
[![Email](https://img.shields.io/badge/Email-zeshan.nasir%40tuta.io-6D28D9?style=flat-square&logo=tutanota&logoColor=white)](mailto:zeshan.nasir@tuta.io)
[![Location](https://img.shields.io/badge/Stockholm%2C_Sweden-%F0%9F%87%B8%F0%9F%87%AA-0d1117?style=flat-square)](https://github.com/ZeshanNasir)

</div>

---

**Hi, I’m Zeshan.** I’m a System Administrator at Optimizely, working at the intersection of IT Support, Infrastructure, and Security. 

My work is making the inputs to automation and AI deterministic, so they stop failing on data quality before they ever fail on models. I focus on bridging infrastructure and AI workflows to drive Service Desk ticket deflection. The lesson underneath all of it: AI initiatives fail without data reliability — an LLM hallucinates the moment it feeds on rotting documentation. To fix that, I engineer the knowledge lifecycle in Confluence — strict metadata labeling, expiration protocols, and standardized templates — so our automation teams (Workato) and AI platforms (Atlassian ROVO) feed on a current, machine-parseable source instead of a guess.

I apply the same discipline to my homelab. The Omega Cluster is where I pressure-test those ideas in infrastructure — zero-trust networking and local-only AI that addresses real compliance constraints (GDPR, HIPAA). Heavily automated (Python, Bash), built to analyze security incidents on-device and keep data exfiltration off the table.

---

## 🏗️ Omega Cluster — the proving ground

My homelab is where I pressure-test enterprise constraints in real infrastructure — data privacy, GPU bottlenecks, compliance, and network attack surface.

**The hardware — two Proxmox nodes plus an off-site quorum arbiter:**

| Node | Role | Runs |
|---|---|---|
| **ms02** *(Intel 235HX · 64 GB DDR5-4800, 128 GB planned)* | AI workhorse | The full AI stack — Qwen3.6-35B LLM, Qdrant vector memory, n8n automation, Grafana/Prometheus/Vaultwarden, PentAGI red-team |
| **hp260** | Control · DR cold-store · homelab | Second quorum node, backup target, utility services (ntfy / miniflux / homepage) |
| **VPS QDevice** | Off-site quorum arbiter | Third Corosync vote — quorum survives either node going down |

Gateway: **OPNsense XG-125** · L2: **HP 1810-24G** VLAN fanout · Tailscale `ts-serve` sidecars front internal apps; nothing is exposed to the internet.

| Architecture Pillar | The Engineering Problem Solved | Status |
|---|---|---|
| **Air-Gapped MLX Engine**<br>*(Mac M4 Pro · 48GB · 273GB/s)* | **Compliance & Speed:** Cloud AI analysis of sensitive logs (Okta/Entra/Azure) is a GDPR/HIPAA problem. Native `ollama-mlx` on Apple Unified Memory runs Gemma4 (26B) and Qwen3.6 (35B MoE) at ~67 / ~61 tok/s locally — one model at a time, by policy, inside the 48 GB budget. Offline analysis of security incidents and access logs with zero cloud exfiltration. | 🟢 Active |
| **CPU-Only Deep Inference**<br>*(ms-ultra-02 · Intel 235HX · 64GB DDR5-4800)* | **GPU independence, measured honestly:** `ik_llama.cpp`, CPU-only (`-ngl 0`, 6 cores, flash-attention, `mlock`), asymmetric KV cache (`K=q8_0` / `V=q4_0`) runs a 35B-A3B MoE in 64 GB of DDR5-4800 (128 GB upgrade planned). **Measured: ~15 tok/s decode** — the memory-bandwidth ceiling, not a tuning gap: an A3B MoE reads ~3B params/token, so throughput is RAM-bandwidth bound and a GPU offload wouldn't change it. Prefill 60–167 tok/s, sub-second TTFT on short prompts. Enough for persistent local RAG. *(measured 2026-06-14)* | 🟢 Locked |
| **Zero-Trust Mesh Topology**<br>*(Proxmox · HP 1810-24G)* | **Attack Surface Reduction:** A "ScaleTail" mesh — 20+ isolated utilities (Vaultwarden, Uptime Kuma) fronted by dedicated Tailscale `ts-serve` sidecars. The cluster is not exposed to the internet; tailnet apps are reachable only via authenticated MagicDNS. | 🟢 Locked |
| **Autonomous Orchestration**<br>*(n8n · Python · Miniflux)* | **Proactive Monitoring:** n8n pipelines and custom `ai-local-skills` connected to RSS/threat feeds aggregate and filter security and threat intelligence, feeding the local analysis environments. The agent (Hermes) proposes with rollback and executes nothing risky without my approval. | 🟢 Locked |
| **Quorum & Resilience**<br>*(Corosync QDevice · OPNsense XG-125)* | **Split-brain prevention (live):** A 2-node Proxmox cluster plus a VPS QDevice gives the third Corosync vote over LAN — quorum holds even though the Tailscale ring is disconnected. Daily off-site backup to Google Drive. Out-of-band recovery (Intel vPro; NanoKVM on ms02) and a fallback WireGuard tunnel are designed and in progress. | 🟢 Live / 🟡 OOB in progress |

---

## Career

```text
2012  System Support Officer       Microtech Industries
2020  Network & System Admin       SV Engineering
2022  Associate System Admin       Optimizely
2026  System Administrator         Optimizely          ← now
      └─ Bridging Support, Security & Infra · Data Reliability for AI
```
