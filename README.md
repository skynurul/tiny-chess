[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/skynurul/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/skynurul/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Tiny Chess

A 4 KB chess engine for the [make.fun tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01).

## Design

- 0x88 mailbox board with incremental Zobrist hashing and make/unmake.
- Tapered PeSTO evaluation: piece-square tables for middlegame and endgame, blended by remaining non-pawn material.
- Principal-variation search (PVS) with a transposition table, null-move pruning, late-move reductions, and quiescence search (captures and promotions, all evasions in check).
- Move ordering: transposition-table move first, then MVV-LVA captures.
- Fixed budget of 100,000 nodes per move and no clock, so every game is fully deterministic and replays move for move.

## Running

```sh
python3 main.py
```

The engine speaks the make.fun environment protocol: it reads `MAKEFUN_ENV_URL`, starts a game, and answers each move. It uses only the Python 3 standard library.

## Local verification

`main.py` is 3,322 bytes, packed from the readable `main.src.py` with the kit's `makefun compress`.

- Perft, start position: depth 3 = 8,902 nodes; depth 4 = 197,281 nodes.
- Trial 0 (practice, local estimate): Elo 1,654 — 5 wins, 0 draws, 1 loss; slowest move 4,798 ms; zero timeouts.

Referral code: `c5vhyhc2`
