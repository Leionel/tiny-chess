[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Leionel/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Leionel/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01: a 4 KB chess engine

`main.py` is the whole engine, packed with the make.fun kit's `compress`
from the readable source `engine.py` (kept beside it, uncommitted; the
bundle carries it). It plays the make.fun gauntlet through the env at
`MAKEFUN_ENV_URL`.

## The engine

- 0x88 board, full legal move generation (castling, en passant, promotion).
- Negamax alpha-beta with iterative deepening to a fixed budget of
90,000 nodes a move (deterministic: no clock, no randomness).
- Quiescence search (captures and promotions; all evasions when in check).
- Transposition table (cleared when a capture or pawn move resets the
fifty-move clock, so no stale repetition scores), killer moves and
MVV-LVA capture ordering. No late-move reductions: a reduced-depth
search accepted as exact inflated scores and hid refutations.
- Evaluation: material + piece-square tables (tapered king table by game
phase) + bishop pair + king pawn shield.
- Repetition detection against the game's own history.

## Files

- `main.py` — the packed engine (4,078 bytes), the entrypoint.
- `engine.py` — the readable source (not committed; the bundle carries it).
- `LICENSE` — MIT. `README.md` — this file.
- `.makefun/owner.json` — the wallet that owns the entry.
