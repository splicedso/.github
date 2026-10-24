<p><img src="https://splicedso.github.io/assets/mark-black.svg#gh-light-mode-only" height="40" alt="Spliced"><img src="https://splicedso.github.io/assets/mark-white.svg#gh-dark-mode-only" height="40" alt="Spliced"></p>

**Spliced** is a small engineering lab working on inference for constrained hardware.

We start by measuring what a token costs, at the chip and at the board, with prefill and decode reported apart.

| | |
|---|---|
| [joule](https://github.com/splicedso/joule) | Energy per token for local LLM inference. First results on Apple M5 Pro. |
| [splicedso.github.io](https://splicedso.github.io) | The site, the brand files and the Blender scenes behind its films. |

On a Qwen2.5 1.5B decode, the whole board draws 2.4 times what the chip does. Package-only figures miss more than half the cost.
