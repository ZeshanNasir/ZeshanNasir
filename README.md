<img src="assets/banner.svg" alt="Zeshan Nasir. Local AI, measured on real hardware." width="100%">

**System administrator in Stockholm. I check what local AI models can really do on a Mac, and publish the raw results.**

## Check a model on your Mac

```sh
git clone https://github.com/ZeshanNasir/local-model-check.git
cd local-model-check
./check
```

[local-model-check](https://github.com/ZeshanNasir/local-model-check) runs one model through 15 small engineering tasks and prints how fast it writes and how many tasks it gets right. It uses only the Python standard library, talks only to Ollama on your Mac, and runs model-written code in a sandbox with no network.

## What it found

Measured on an M4 Pro with 48 GB, 2026-11-02, Ollama 0.40.13. Each model ran every task three times. The raw files are in the repository.

| Model | Speed | Tasks passed |
| :--- | ---: | ---: |
| `qwen3.6:35b-mlx` | 67 tok/s | 37/45 |
| `gemma4:26b-mlx` | 56 tok/s | 42/45 |
| `qwen3.8:27b-mlx` | 28 tok/s | 42/45 |
| `flint:40b-a2b-qat-int4` | 98 tok/s | 33/45 |

From the earlier 2026-10-09 run:

- **Long prompts are slow.** At about 67,000 tokens the first word took between 137 s and 704 s.
- **Running the tests changes the result.** A model that failed a code fix when answering in one go fixed it in three of three sessions when it could run the tests.
- **Local is not automatically private.** Ollama stayed on the machine. The coding agent around it also connected to outside servers whose purpose I could not identify.

## My two machines

The tool above covers the first machine only.

### Workstation: MacBook Pro M4 Pro, 48 GB

- **Runs:** `flint` and `nemotron-3.5-bolt`, through Ollama.
- **Used for:** coding and code review.
- **Measured:** first word after 3.6 s for a 3.5K-token prompt. A 48K-token prompt answered correctly in 97 s. 22 GB of model in memory, no swap growth in these runs.

### Always-on server: Minisforum MS-02 Ultra, Core Ultra 5

- **Runs:** `Ling-3.0-tiny`, through `ik_llama.cpp`.
- **Used for:** automation that runs around the clock.
- **Measured:** first word after 0.176 s for a short prompt. Set up for a 131K-token context window.

> **Cost model:** a $3,500–$4,000 Mac over four years is $73–$83 a month, with no per-token fee for work that runs locally.

---

[Website ↗](https://zeshannasir.com) &nbsp;·&nbsp; [LinkedIn ↗](https://linkedin.com/in/zeshan-nasir)
