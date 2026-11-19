# makefun-tiny-chess-01-v2

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Alfatih15/makefun-tiny-chess-01-v2/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Alfatih15/makefun-tiny-chess-01-v2/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB chess engine in Python, v2: stronger than v1 (measured baseline Elo 1279 on practice trial-0). 0x88 board, alpha-beta with transposition table, iterative deepening, quiescence, null-move, LMR, PVS, killer + history heuristics, bishop pair, passed pawns, endgame king table. Fixed 100,000 nodes/move, deterministic, stdlib only.

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=hjff56h1&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>

## Engine

`main.py` is 4,066 bytes: the kit's `makefun compress` packs the readable source (`engine_src.py`, kept beside it uncommitted) into an LZMA payload. Perft exact: startpos 20/400/8902/197281, kiwipete 48/2039/97862. Differential readable vs packed: same move on 8/8 positions.
