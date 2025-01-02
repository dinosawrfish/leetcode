## Approach

Given an nested list of moves, knowing that the first player plays X, and then the second player plays O on a tick tack toe game, I need to determine the winner or draw of the game.

I initially started thinking about the number of moves recorded defining the winner. The grid is n x n so if there are n moves and there is no winner then it is a draw.


This assumes that the moves records a finished game which is not true. The game can still be without a winner so it needs to return pending.

I need to find a way to define a win. (Assuming a 3 x 3 game)
- Horizontal: [r, 0], [r, 1], [r, 2] r being row
    - essentially there needs to be three values at the same row
- Vertical: [0, c], [1, c], [2, c] c being col
    - needs to be three values at the same col
- diagonals: [0, 0], [1, 1], [2, 2]
    - row is equal to col
- anti diagonal: [0, 2], [1, 1], [2, 0]
    - in this case row plus col is 2 or row + col = n - 1

It would work best to simulate the game and check if there is a winner each round. The players need to cancel out so I can assign player x as 1 and player o as -1.

I'll need to represent the results of the game by rows, cols, diag, and antidiag and check when they add up to n or -n for a winner.

## Code

``` python
class Solution:
    def tictactoe(self, moves: List[List[int]]) -> str:

        rows = [0, 0, 0]
        cols = [0, 0, 0]
        diag = 0
        anti_diag = 0

        player = 1

        for row, col in moves:
            rows[row] += player
            cols[col] += player

            if row == col:
                diag += player
            if row + col == 2:
                anti_diag += player

            player *= -1

        winning_moves = 3
        stats = rows + cols + [diag] + [anti_diag]

        if winning_moves in stats:
            return "A"
        elif winning_moves*-1 in stats:
            return "B"

        elif len(moves) == winning_moves**2:
            return "Draw"

        return "Pending"
```

## Runtime/Memory

Runtime: O(n) n being the number of values in moves

Memory: O(1) assuming the board is always 3x3, for an n x n board the space complexity is O(n) n being the dimension of the board since we do create two lists to record row and col results based on nth dimensions