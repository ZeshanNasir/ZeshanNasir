<img src="assets/banner.svg" alt="Zeshan Nasir. Local AI, measured on real hardware." width="100%">

**System administrator in Stockholm. I test local AI models on my own hardware and publish the raw results.**

## Try it

```sh
git clone https://github.com/ZeshanNasir/ai-local.git && cd ai-local && ./lab
```

[ai-local](https://github.com/ZeshanNasir/ai-local) runs one local model through 15 small engineering tasks and prints its speed and how many tasks it passed. It needs a Mac with Apple Silicon, Python 3.10 or newer, and Ollama.

## What it found

Measured on an M4 Pro with 48 GB on 2026-10-09. Each model ran every task three times. The raw files are in the repository.

| Model | Speed | Tasks passed |
| :--- | ---: | ---: |
| `qwen3.6:35b-mlx` | 68 tok/s | 43/45 |
| `gemma4:26b-mlx` | 60 tok/s | 42/45 |
| `qwen3.8:27b-mlx` | 26 tok/s | 42/45 |

- **Long prompts are slow.** At about 67,000 tokens the first word took between 137 s and 704 s.
- **Running the tests changes the result.** A model that failed a code fix when answering in one go fixed it in three of three sessions when it could run the tests.
- **Local is not automatically private.** Ollama stayed on the machine. The coding agent around it also connected to outside servers whose purpose I could not identify.

## Two machines

[ai-local](https://github.com/ZeshanNasir/ai-local) covers the workstation only. The figures below come from my own test runs and lab, not from that repository.

### Workstation · MacBook Pro M4 Pro, 48 GB

| Metric | Specification |
| :--- | :--- |
| **Runtime** | Ollama (MLX), listening on loopback · `flint:40b` · `nemotron:e4b` |
| **Job** | Interactive engineering: code audit, subagent loops |
| **Measured** | 100/100 Tier S · 1,176–1,776 tok/s prefill · 82–105 tok/s decode · 22 GB weights in RAM, zero swap |

### Continuous ops · Minisforum MS-02 Ultra (Core Ultra 5, 6 P-cores)

| Metric | Specification |
| :--- | :--- |
| **Runtime** | `ik_llama.cpp` (AVX-VNNI) · `Ling-3.0-tiny` (MoE) |
| **Job** | 24/7 services: MCP tool-calling, n8n triage, Home Assistant |
| **Measured** | 0.176 s TTFT · 511 tok/s prefill · 39.8 tok/s decode · 131K context in ~7.1 GiB RAM · ~20 W wall power |

> **Cost model:** A workstation amortized at about $75–$80 per seat per month over 4 years replaces variable token bills with $0.00 marginal cost per token for routine developer loops.

---

[Website ↗](https://zeshannasir.com) &nbsp;·&nbsp; [LinkedIn ↗](https://linkedin.com/in/zeshan-nasir)
