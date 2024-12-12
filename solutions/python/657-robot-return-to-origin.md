## Approach
Given a string with each char at i position is the ith move of a robot, I need to determine if after all the moves, the robot is back at the original position.

The robot moves in a 2D plane.
The moves are
- `'R'` moves to right
- `'L'` moves to left
- `'U'` moves up
- `'D'` moves down

I do not need to record its path since I only care where it is in the end. R/L and U/D cancel each other out. So all I need to is iterate through moves and add/substract (x, y) x based on R/L, and y based on U/D.

Return true if (0, 0) false otherwise.

## Code
``` python
def judgeCircle(self, moves: str) -> bool:

        movement = {
            'R': (1, 0),
            'L': (-1, 0),
            'U': (0, 1),
            'D': (0, -1)
        }

        robot = (0, 0)

        for move in moves:
            robot = (robot[0] + movement[move][0], robot[1] + movement[move][1])

        return robot == (0, 0)
```


## Time/Space Complexity
Runtime: O(n) n being the length of string moves since we have to iterate per chr to move the robot
Space: O(1) robot is constant space
