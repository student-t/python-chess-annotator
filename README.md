# python-chess-annotator
Takes a PGN file as an argument and annotates the games in that file using an
engine.

Computes average centipawn loss (ACPL) for each side and stores it in the
header.

The result will be printed on standard output (the file on disk will be
unchanged).

## Installation
```
pip3 install chess-annotator
```

## Dependencies
You will need a UCI[[1]] chess engine for analysis. stockfish[[2]] is the
default.

Requires python-chess[[3]] by Niklas Fiekas:
```
pip3 install python-chess
```

## Usage
```
$ python3 -m annotator -h
usage: annotator [-h] --file FILE.pgn [--engine ENGINE] [--time MINUTES]
                 [--verbose]

takes chess games in a PGN file and prints annotations to standard output

optional arguments:
  -h, --help            show this help message and exit
  --file FILE.pgn, -f FILE.pgn
                        input PGN file
  --engine ENGINE, -e ENGINE
                        analysis engine (default: stockfish)
  --time MINUTES, -t MINUTES
                        how long to spend on each game (default: 1)
  --verbose, -v         increase verbosity

$ python3 -m annotator -f caruana-kasparov.pgn -t 15
[Event "Ultimate Blitz Challenge"]
[Site "St. Louis, MO USA"]
[Date "2016.04.29"]
[Round "18.1"]
[White "Fabiano Caruana"]
[Black "Garry Kasparov"]
[Result "0-1"]
[EventDate "2016.04.28"]
[ECO "A05"]
[WhiteElo "2795"]
[BlackElo "2812"]
[PlyCount "74"]
[Opening "King's Indian Attack: Symmetrical Defense"]
[White ACPL "252"]
[Black ACPL "141"]
[Annotator "Stockfish 8 64 POPCNT"]

{ Stockfish 8 64 POPCNT } 1. Nf3 Nf6 2. g3 g6 { A05 King's Indian Attack:
Symmetrical Defense } 3. Bg2 Bg7 4. O-O O-O 5. c4 d6 6. b3 e5 7. Bb2 c5 8. e3
Nc6 9. Nc3 Bf5 10. d4 e4 11. Ne1 Re8 12. Nc2 h5 13. Qd2 h4 14. Ba3 $6 { -1.13 }
( 14. h3 g5 15. g4 Bg6 16. Rad1 Qe7 17. Qe2 a6 18. Ba3 a5 { 0.19/25 } ) 14...
b6 $6 { -0.04 } ( 14... Nh7 15. Nd5 Ng5 16. Bb2 Rc8 17. Rac1 Ne7 18. Nf4 h3 19.
Bh1 { -1.11/24 } ) 15. Rfd1 $6 { -1.15 } ( 15. h3 d5 16. g4 Be6 17. cxd5 Nxd5
18. Nxe4 f5 19. gxf5 gxf5 { 0.00/26 } ) 15... Bg4 16. Rdc1 Qd7 17. b4 Qf5 18.
Bb2 Rad8 19. Nb5 Bf3 20. d5 Ne5 $6 { -1.66 } ( 20... Nxb4 21. Ne1 Bxg2 22.
Nxg2 Nd3 23. Nxh4 Qh3 24. Bxf6 Bxf6 25. f4 { -3.14/25 } ) 21. Bxe5 Rxe5 22.
Ne1 hxg3 23. fxg3 Bh6 24. Rab1 Kg7 $6 { -1.08 } ( 24... Qh5 25. Rb3 Rf5 26.
bxc5 dxc5 27. Rc2 Ng4 28. h3 Bxg2 29. Kxg2 { -2.48/24 } ) 25. Rb3 Qh5 26. h3
$6 { -3.08 } ( 26. bxc5 bxc5 27. Nxa7 Rh8 28. h4 Qg4 29. Nc6 Rh5 30. Qf2
Bd1 { -2.00/23 } ) 26... Nh7 $2 { -1.37 } ( 26... Rg5 27. Qf2 { -2.89/24 })
27. g4 Bxg4 28. hxg4 Qxg4 29. Qd1 $4 { -5.69 } ( 29. Qb2 Ng5 30. Nxd6 Qg3
31. Nf5+ gxf5 32. Kf1 Nf3 33. Qf2 Nh2+ { -2.30/24 } ) 29... Qg3 30. Qe2 Ng5
31. Kh1 Rh8 32. Nxd6 Kg8 33. bxc5 Bf8+ 34. Kg1 Nh3+ 35. Kf1 Bxd6
36. cxd6 Rf5+ 37. Nf3 Rxf3+ 0-1
```

## To-do
- Add support for variants (chess960, crazyhouse, etc)
- Provide an option to analyze moves from one player only

## Legal
This program is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation, either version 3 of the License, or (at your
option) any later version.

You should have received a copy of the GNU General Public License along
with this program.  If not, see <http://www.gnu.org/licenses/>.

[1]: https://chessprogramming.wikispaces.com/UCI
[2]: https://stockfishchess.org/download/
[3]: https://github.com/niklasf/python-chess
[4]: https://github.com/chriskiehl/Gooey
<!-- vim: ft=markdown -->
