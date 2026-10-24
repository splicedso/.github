<p><img src="https://splicedso.github.io/assets/mark-black.svg#gh-light-mode-only" height="40" alt="Spliced"><img src="https://splicedso.github.io/assets/mark-white.svg#gh-dark-mode-only" height="40" alt="Spliced"></p>

**Spliced** is a small research lab for efficient inference. We measure what it costs to run a model, in watts and joules as well as seconds, and publish the method, the code and the raw data with every result.

### Research areas

| | |
|---|---|
| **Inference engineering** | Where decode time and energy go: memory bandwidth, kernels, quantization formats, batching, KV cache, and how inference clusters are designed. |
| **Data science** | Measurement you can trust: repeated runs, held-out validation, models whose coefficients have to make physical sense. |
| **Software engineering** | Small, readable, open tools that make every measurement repeatable. |

Later: electrical engineering, starting with an open power-measurement board.

### Published notes

1. [Fewer bits is not fewer joules](https://github.com/splicedso/joule/blob/main/notes/2026-10-formats-and-batching.md). Eight quantization formats and batch sizes 1 to 8, energy at the chip and at the board. Chip-only measurement misranks F16 by 2x; batch 2 saves 1% per token and batch 8 saves 72%.
2. [Where the joules go](https://github.com/splicedso/joule/blob/main/notes/2026-10-roofline-and-energy-model.md). A decode roofline from measured bandwidth (266 GB/s) and a leave-one-out-validated energy model. Its residuals isolate the cost of unpacking each format.
3. [Does it hold?](https://github.com/splicedso/joule/blob/main/notes/2026-10-scale-and-runtime.md) The study at 7B, where every finding replicates and the hardware is used better, and in MLX, where repeat runs do not yet agree.

### Tools

- [joule](https://github.com/splicedso/joule): energy per token for local inference, prefill and decode apart, chip and board, no sudo.

### In progress

- The same study on a Windows laptop, on battery.
- Why MLX repeat runs disagree when llama.cpp's do not.
- Per-kernel energy: timing and power-sampling each format's matrix-vector kernel alone.
- Speculative decoding: does it save joules, or only seconds?
- Cluster design: tokens per megawatt-hour across GPU generations, from public specs and a roofline, checked against MLPerf.

We are a company, with the research in the open. If you build hardware or ship models to devices and want a model made to run well on yours, and measured honestly, open an issue on [joule](https://github.com/splicedso/joule/issues).

[splicedso.github.io](https://splicedso.github.io)
