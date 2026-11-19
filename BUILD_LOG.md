# BUILD_LOG — tiny-chess-01 v2

## Entry

- `main.py` **4,066 B** (cap 4,096), packed by the kit's
  `makefun compress` from readable `engine_src.py` (13,927 B).
  Round-trip: decompresses byte-identical.
- Snapshot: main.py 4,066 + LICENSE 1,096 + README 1,448 + this
  file + `.makefun/owner.json` 57 — under the 8,192 cap.
- Wallet: `Cfdgeggmd6ij5dLpqwmqAaGExTbi4JPZJYcRdi4iSjSW`.

## Baseline (v1 slim, measured)

- Practice trial-0 (local env + scorer): **Elo 1279**,
  3 wins / 0 draws / 3 losses, spare_plies 289.
  Wins vs depth-2/3/4, losses vs nodes-100k/250k/500k.
- Trial-1 running at time of writing.

## Engine v2 vs v1

- Node budget 70,000 → 100,000 per move (fixed, deterministic).
- Added back: bishop pair (+30), history heuristic (capped 4000),
  passed-pawn bonus, endgame king table (queens off).
- Kept: 0x88, TT, null-move R=2, LMR, PVS, check extension,
  killer moves, Michniewski PSTs, iterative deepening.

## Verification

- Perft exact: startpos 20/400/8902/197281, kiwipete
  48/2039/97862, pos3 14/191/2812/43238, pos4 6/264/9467,
  pos5 44/1486/62379.
- Differential readable vs packed: same move on 8/8 positions.
- Eval sanity: startpos 0, passed-pawn bonus +50, bishop pair
  +30, endgame king centralises.
- Trials vs the kit's practice instances: see below.
