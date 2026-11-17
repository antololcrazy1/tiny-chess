# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/antololcrazy1/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/antololcrazy1/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

**Tiny Chess** — a chess engine in 4,003 bytes of Python for make.fun's "Build the strongest chess engine in 4 KB of Python" bounty.

## How it plays

- 0x88 board, full legal move generation (castling, en passant, all four promotions), verified against perft counts.
- Negamax alpha-beta with a transposition table, killer moves, MVV-LVA capture ordering and quiescence search (captures only, with delta pruning), iterative deepening to a fixed 50,000-node budget per move — never a clock, so replays are byte-identical.
- Evaluation mirrors the house engine's piece-square tables (material + positional terms, king phase interpolation, bishop-pair bonus).
- It talks to the env over HTTP (`MAKEFUN_ENV_URL`): `POST /game` for the position, `POST /move` to play.

Local practice trials against the house gauntlet: trial-0 2W 2D 2L (Elo ≈1,275), trial-1 2W 3D 1L (Elo ≈1,360).

## Source

`main.py` is the whole engine, packed with lzma as the brief allows (the same packing the house baseline uses). The readable source it was packed from is 10,245 bytes; it was minified and packed to 4,003 bytes. Run it with Python 3.13, standard library only.

---

<sub>Entered on [make.fun](https://make.fun/?ref=cde26xpc&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
