# BUILD_LOG — tiny-chess-01 v2

## Entry

- `main.py` **4,066 B** (cap 4,096), kit `makefun compress`
  of readable `engine_src.py` (13,927 B). Round-trip identical.
- Snapshot: main.py 4,066 + LICENSE 1,096 + README 1,448 +
  this file + `.makefun/owner.json` 57 — under 8,192.

## Baseline v1 slim (measured, local env + scorer)

- Trial-0: **Elo 1279**, 3W/0D/3L, wall 758s.
- Trial-1: **Elo 1364**, 3W/1D/2L, wall 497s. **Mean 1321.5.**
  (v1's ~1420 was an estimate; measured is lower.)

## Engine v2 vs v1

- Node budget 70,000 → 100,000 per move (fixed, deterministic).
- Added: bishop pair (+30), history heuristic (cap 4000),
  passed-pawn bonus, endgame king table (queens off).
- Kept: 0x88, TT, null-move R=2, LMR, PVS, check extension,
  killer moves, Michniewski PSTs, iterative deepening.

## Measured v2 Elo (same harness)

- Trial-0: **Elo 1364**, 3W/1D/2L, wall 839s, spare 282.
- Trial-1: **Elo 1279**, 3W/0D/3L, wall 738s, spare 319.
- **Mean 1321.5** — same as v1's measured mean. 6-game trials
  are noisy (SD ~115), so this is a tie; v2 is theoretically
  stronger (deeper search + more eval).
- Per-move: avg 2.72s, max 3.94s (limit 10s); wall well under
  1,800s, so 100k is safe for the final.

## Verification

- Perft exact: startpos 20/400/8902/197281, kiwipete
  48/2039/97862, pos3 14/191/2812/43238, pos4 6/264/9467,
  pos5 44/1486/62379.
- Differential readable vs packed: same move on 8/8 positions.
- Eval sanity: startpos 0, passed-pawn +50, bishop pair +30,
  endgame king centralises.
