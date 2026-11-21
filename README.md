### Hi, I'm LiquidLava1990

I run large language models on an 8-card **Intel Gaudi 2** server and publish the recipes that work, and the ones that didn't.

Each repo below is built on that model's **champion** config, the best setup I've measured. It includes the real scripts, configs, kernels and patches, plus the measured numbers. Model weights are not included.

### Gaudi 2 recipes

| Repo | Model | Status | Champion result |
|---|---|---|---|
| [gaudi2-glm-5.3-flash](https://github.com/LiquidLava1990/gaudi2-glm-5.3-flash) | GLM-5.3-Flash, FP8 | In production | 10.76 tok/s per agent with 16 agents on one 4-card replica, 524K context |
| [gaudi2-glm-5.2](https://github.com/LiquidLava1990/gaudi2-glm-5.2) | GLM-5.2, int4 experts (AutoRound) | Superseded | 14.77 tok/s single stream, 303 tok/s at 64 concurrent |
| [gaudi2-minimax-m3](https://github.com/LiquidLava1990/gaudi2-minimax-m3) | MiniMax-M3, FP8 | Reference | about 405 tok/s at 128 concurrent, 128/128 coherent |
| [gaudi2-qwen3.6-27b](https://github.com/LiquidLava1990/gaudi2-qwen3.6-27b) | Qwen3.6-27B, FP8 | Reference | 1,265 tok/s at 64 concurrent |
| [gaudi2-glm-5.3-full](https://github.com/LiquidLava1990/gaudi2-glm-5.3-full) | GLM-5.3 Full | Abandoned | What was tried, what crashed, and what to avoid |
| [gaudi2-common](https://github.com/LiquidLava1990/gaudi2-common) | Shared parts | Used by all | Base images, launchers, custom HPU kernels, vLLM patches, health checks |

### The hardware

- 8x Intel Gaudi 2 (HL-225), 96 GB HBM each
- 2-socket Xeon, about 500 GB RAM
- Driver, containers and firmware: Gaudi software 1.24.2, card firmware 62.6.2
- vLLM with the vllm-gaudi plugin

Everything is Apache-2.0. Issues and questions are welcome on any repo.
