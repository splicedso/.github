<p><img src="https://splicedso.github.io/assets/mark-black.svg#gh-light-mode-only" height="40" alt="Spliced"><img src="https://splicedso.github.io/assets/mark-white.svg#gh-dark-mode-only" height="40" alt="Spliced"></p>

**Spliced** is a small research lab for efficient inference. We measure what it costs to run a model, in watts and joules as well as seconds, and publish the method, the code and the raw data with every result.

### Research areas

| | |
|---|---|
| **Inference engineering** | Where decode time and energy go: memory bandwidth, kernels, quantization formats, batching, KV cache, and how inference clusters are designed. |
| **Data science** | Measurement you can trust: repeated runs, held-out validation, models whose coefficients have to make physical sense. |
| **Software engineering** | Small, readable, open tools that make every measurement repeatable. |

### Published notes

1. [Fewer bits is not fewer joules](https://github.com/splicedso/joule/blob/main/notes/2026-10-formats-and-batching.md). Eight quantization formats and batch sizes 1 to 8, energy at the chip and at the board. Chip-only measurement misranks F16 by 2x; batch 2 saves 1% per token and batch 8 saves 72%.
2. [Where the joules go](https://github.com/splicedso/joule/blob/main/notes/2026-10-roofline-and-energy-model.md). A decode roofline from measured bandwidth (266 GB/s) and a leave-one-out-validated energy model. Its residuals isolate the cost of unpacking each format.
3. [Does it hold?](https://github.com/splicedso/joule/blob/main/notes/2026-10-scale-and-runtime.md) The study at 7B, where every finding replicates and the hardware is used better, and in MLX, where repeat runs do not yet agree.
4. [Two machines, one token](https://github.com/splicedso/joule/blob/main/notes/2026-10-two-machines.md) The study on a Windows laptop with an RTX 5070 Ti, on battery. Q4_0 wins on both; a 4-bit token costs the same whole-machine energy on both; one Mac finding does not transfer.
5. [The cost of unpacking](https://github.com/splicedso/joule/blob/main/notes/2026-10-kernel-energy.md) Each format's kernel measured alone. Q4_0 and Q4_K read identical bytes at identical speed; Q4_K's unpacking costs 40% more chip energy.
6. [Small models pay more per weight](https://github.com/splicedso/joule/blob/main/notes/2026-10-model-width.md) Five formats across 0.5B to 7B. A weight in a 0.5B model costs up to 1.6 times one in a 7B; Q4_0 is cheapest at every width.
7. [Faster is not cheaper](https://github.com/splicedso/joule/blob/main/notes/2026-10-speculative-decoding.md) Speculative decoding can be faster and cost more energy at once; copying from the context on an edit costs 32% of plain decoding.
8. [Tokens per megawatt-hour](https://github.com/splicedso/joule/blob/main/notes/2026-10-tokens-per-megawatt-hour.md) Every MLPerf LLM result with measured wall power: a B200 server buys 2.7 times the tokens per joule of an H100 NVL one.
9. [One flag fixes speculative decoding's energy problem](https://github.com/splicedso/joule/blob/main/notes/2026-10-speculative-threshold.md) A draft confidence threshold of about 0.5 removes the energy penalty on every task tested.
10. [The same token, plugged in, and under batching](https://github.com/splicedso/joule/blob/main/notes/2026-10-windows-ac-and-batching.md) A discrete NVIDIA GPU plugged in: 34 to 46% faster for 23 to 33% more energy per token, and at its power ceiling from batch 1, so the second request saves 43% where on the Mac it saved 1%.

All measurements in one table: [the Spliced dataset](https://splicedso.github.io/data/).

### Tools

- [joule](https://github.com/splicedso/joule): energy per token for local inference, prefill and decode apart, no admin rights. macOS (chip and board) and Windows with NVIDIA (GPU and battery).

### In progress

- Why MLX repeat runs disagree when llama.cpp's do not.
- Model shape: separating width from depth and vocabulary in the small-model penalty.
- Speculative decoding on an NVIDIA GPU, and draft thresholds below 0.5.
- Serving energy at batch, with a real serving engine under realistic load.

We are a company, with the research in the open. If you build hardware or ship models to devices and want a model made to run well on yours, and measured honestly, open an issue on [joule](https://github.com/splicedso/joule/issues).

[splicedso.github.io](https://splicedso.github.io) · [LinkedIn](https://www.linkedin.com/company/splicedso)
