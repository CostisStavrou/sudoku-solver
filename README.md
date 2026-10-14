# Sudoku Solver

A backtracking sudoku solver in Python. It fills the most constrained cell first and detects puzzles that are invalid or have no solution.

**Built:** January 2024, as Year 1 coursework for my Computer Science degree at the University of Bath.

## How it works

1. **Validate** the starting grid. A digit repeated in a row, column or 3×3 box means the puzzle is invalid.
2. **Choose the most constrained cell**: the empty cell with the fewest legal digits (the minimum-remaining-values heuristic).
3. **Backtrack**: try each legal digit, recurse, and undo the move if it leads to a dead end. If every option fails, the puzzle has no solution and the solver returns a grid of `-1`.

## Results

Tested on 60 puzzles. From "easy" upwards, a third of each set is invalid or unsolvable.

| Difficulty | Correct | Average time | Slowest |
|---|---|---|---|
| Very easy | 15/15 | < 0.01 s | < 0.01 s |
| Easy | 15/15 | < 0.01 s | < 0.01 s |
| Medium | 15/15 | < 0.01 s | 0.01 s |
| Hard | 15/15 | ~3.5 s | ~14 s |

All 60 are solved correctly, but hard puzzles are slow. At every step the solver rescans the whole board to count each empty cell's options. The obvious next step would be to track each row's, column's and box's remaining candidates incrementally (constraint propagation) instead of recomputing them.

## Run it

```bash
pip install -r requirements.txt
jupyter notebook sudoku_solver.ipynb
```

`data/` holds the 60 test puzzles and their solutions, which came with the coursework.
