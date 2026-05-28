<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=16&duration=2800&pause=900&color=00FF87&center=true&vCenter=true&width=680&lines=System+Administrator+%40+Optimizely;Building+Sovereign+Local+AI+Environments;Data+Reliability+Engineering+for+AI;Zero-Trust+ScaleTail+Mesh+Architecture;Removing+manual+toil+through+automation)](https://github.com/ZeshanNasir)

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

My primary mandate is to architect solutions that permanently resolve systemic issues and eliminate manual toil. I focus on bridging the gap between infrastructure and modern AI workflows to drive Service Desk ticket deflection. I’ve learned that AI initiatives fail without data reliability; an LLM will hallucinate if it feeds on rotting documentation. To solve this, I engineer the knowledge lifecycle in Confluence—enforcing strict metadata labeling, expiration protocols, and standardized templates. By defining these strict data schemas, I provide the deterministic foundation required by our automation teams (using Workato) and AI platforms (like Atlassian ROVO) to safely deploy ticket deflection without the risk of hallucination.

I apply this same rigor to my sovereign infrastructure. I use the Omega Cluster to architect zero-trust networks and experiment with local AI and zero-trust networking, finding ways to solve enterprise compliance headaches (GDPR, HIPAA, SOC2/SD). My environments are heavily automated (Python, Bash) and built to proactively research security incidents and eliminate data exfiltration risks.

---

## 🏗️ The Sovereign Laboratory (Omega Cluster)

My personal infrastructure is a proving ground for solving enterprise constraints—specifically data privacy, GPU bottlenecks, compliance, and network attack surfaces.

| Architecture Pillar | The Engineering Problem Solved | Status |
|---|---|---|
| **Air-Gapped MLX Engine**<br>*(Mac M4 Pro · 48GB · 276GB/s)* | **Compliance & Speed:** Cloud AI analysis of sensitive data (Okta/Azure logs) violates GDPR/HIPAA compliance. I leverage native `ollama-mlx` and Apple Unified Memory to run Gemma4 (26B) and Qwen3.6 (35B MoE) models at 67-70 tok/s locally. This provides agentic-speed, offline analysis of security incidents and access logs with zero cloud exfiltration risk. | 🟢 Active |
| **CPU-Only Deep Inference**<br>*(ms-ultra-02 · Intel 235HX · 96GB)* | **GPU Independence:** Persistent AI workloads shouldn't require massive GPU budgets. I heavily tune `ik_llama.cpp` (Multi-Token Prediction, P-core pinning, `q8_0` KV cache) to force 35B models into standard DDR5 RAM. This achieves 47 tok/s prefill and 14 tok/s generation for persistent local RAG and document intelligence. | 🟢 Locked |
| **Zero-Trust Mesh Topology**<br>*(Proxmox · HP ProCurve 24-Port)* | **Attack Surface Reduction:** Traditional reverse proxies are vulnerabilities. I deploy a "ScaleTail" mesh topology. 20+ isolated utilities (Vaultwarden, Uptime Kuma) are fronted by dedicated Tailscale sidecars. The entire cluster is invisible to the internet, addressable only via authenticated MagicDNS to prevent configuration drift. | 🟢 Locked |
| **Autonomous Orchestration**<br>*(n8n · Python · Miniflux)* | **Proactive Monitoring:** Manual research is slow. I use n8n automated pipelines and custom `ai-local-skills` connected to RSS feeds to continuously aggregate and filter security vulnerabilities and threat intelligence, feeding relevant data directly into my local analysis environments. | 🟢 Locked |
| **High Availability & OOB**<br>*(Corosync Quorum · OPNsense XG-125)* | **Resilience:** Building a 3-node Corosync quorum using a cloud VPS (QDevice) to prevent split-brain failure. Disaster recovery relies on hardware-level Out-of-Band (OOB) management (Intel vPro on hp260, upcoming NanoKVM on ms02) and a fallback WireGuard tunnel on the firewall to ensure constant remote access. | 🟡 In Progress |

---

## Career

```text
2012  System Support Officer       Microtech Industries
2020  Network & System Admin       SV Engineering
2022  Associate System Admin       Optimizely
2026  System Administrator         Optimizely          ← now
      └─ Bridging Support, Security & Infra · Data Reliability for AI
```
