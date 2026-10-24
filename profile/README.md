<p><img src="https://splicedso.github.io/assets/mark-black.svg#gh-light-mode-only" height="40" alt="Spliced"><img src="https://splicedso.github.io/assets/mark-white.svg#gh-dark-mode-only" height="40" alt="Spliced"></p>

**Spliced** is a small research lab for efficient inference. We measure what it costs to run a model, in watts and joules as well as seconds, and publish the method, the code and the raw data with every result.

### Research areas

| | |
|---|---|
| **Inference engineering** | Where decode time and energy go: memory bandwidth, kernels, quantization formats, batching, KV cache. |
| **Data science** | Measurement you can trust: repeated runs, held-out validation, models whose coefficients have to make physical sense. |
| **Electrical engineering** | The power path itself: chip versus board, sensing, and our own measurement hardware. |

### Published notes

1. [Fewer bits is not fewer joules](https://github.com/splicedso/joule/blob/main/notes/2026-10-formats-and-batching.md). Eight quantization formats and batch sizes 1 to 8, energy at the chip and at the board. Chip-only measurement misranks F16 by 2x; batch 2 saves 1% per token and batch 8 saves 72%.
2. [Where the joules go](https://github.com/splicedso/joule/blob/main/notes/2026-10-roofline-and-energy-model.md). A decode roofline from measured bandwidth (266 GB/s) and a leave-one-out-validated energy model. Its residuals isolate the cost of unpacking each format.

### Tools

- [joule](https://github.com/splicedso/joule): energy per token for local inference, prefill and decode apart, chip and board, no sudo.

### In progress

- The same study on a 7B model and on MLX, and on a Windows laptop.
- Per-kernel energy: timing and power-sampling each format's matrix-vector kernel alone.
- Speculative decoding: does it save joules, or only seconds?
- An open power-measurement board (INA228 current sensing, about 1 kHz) to replace the 1 Hz board reading.

We are a company, with the research in the open. If you build hardware or ship models to devices and want a model made to run well on yours, and measured honestly, open an issue on [joule](https://github.com/splicedso/joule/issues).

[splicedso.github.io](https://splicedso.github.io)
