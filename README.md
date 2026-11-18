# tiny-chess-01 entry

[![tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun)
[![rank](https://make.fun/badge/tiny-chess-01/sofikulxdd-web/tiny-chess-engine/rank.svg)](https://make.fun)
[![reward](https://make.fun/badge/tiny-chess-01/sofikulxdd-web/tiny-chess-engine/reward.svg)](https://make.fun)

An original chess engine for make.fun's tiny-chess-01: `main.py` is the
whole engine, 3,477 bytes of Python 3.13 (standard library only), stored
as a zlib payload and its unpacker.

- 10x12 mailbox board, flipped so the side to move is always uppercase
- material plus tapered piece-square tables built from formulas
- iterative-deepening alpha-beta (PVS) with a transposition table,
  null-move pruning, late-move reductions, futility and reverse futility
  pruning, killer moves, check extension and quiescence search
- repetition-aware, so it steers for draws only when it is worse
- deterministic: each move searches at most 100,000 nodes and never reads
  a clock; once 15M nodes have been used in a trial, the cap drops to
  20,000 nodes a move to keep the trial inside its wall time

It plays the gauntlet over HTTP through `MAKEFUN_ENV_URL`.
