# Tiny Chess

A 4 KB chess engine for the make.fun tiny-chess-01 bounty.

## Design

- 0x88 mailbox board with incremental Zobrist hashing and make/unmake.
- Tapered PeSTO evaluation: piece-square tables for middlegame and
  endgame, blended by the remaining non-pawn material.
- Iterative-deepening principal-variation search with a transposition
  table, null-move pruning, late-move reductions, and quiescence search
  (captures and promotions, all evasions in check).
- Move ordering: transposition-table move first, then MVV-LVA captures.
- Fixed node budget per move, so every game is fully deterministic and
  replays move for move.

## Running

The engine speaks the make.fun environment protocol: it reads
`MAKEFUN_ENV_URL`, starts a game, and answers each move. It uses only
the Python 3 standard library.

## Size

`main.py` is a single self-contained file under 4,096 bytes.

## Local verification

Trial 0 (practice, local estimate): Elo 1,654 — 5 wins, 0 draws, 1 loss; slowest move 4,798 ms; zero timeouts.
