# Tiny Chess 01 entry

A chess engine in at most 4,096 bytes of Python 3.13, written for the
make.fun tiny-chess-01 competition. It plays the house gauntlet through
the env (POST /game, POST /move), one game after another.

Design: 0x88 board, fully legal move generation (castling, en passant,
promotions), negamax alpha-beta search with PVS, quiescence search with
check evasions and delta pruning, late move reductions, a transposition
table used for move ordering, killer moves, zobrist position keys, and a
material + piece-square evaluation with pawn-structure terms. It searches
a fixed node budget per move (never a clock), so replays match exactly.

main.py is the whole engine. To fit the size cap it carries the engine
source as an lzma payload with a small unpacker, the packing the
competition rules explicitly allow; the payload and unpacker together
are the 3,958 bytes. The readable source was developed and perft-tested
in the open (start position, Kiwipete and en-passant-pin suites all
match the known node counts exactly).
