## Approach
Given a set of instructions, in which each string is a instruction to either move a robot one unit, or turn it left or right 90 degrees, I need to find if the set of instructions repeated infinitely would have the robot repeat a circle.

The first thing that comes to mind are cyclic graphs. The problem is essentially asking if one would exist given the instructions.

It does not seem doable to brute force and repeat the instructions x amount of times until we see the robot return to 0, 0 or not.

What patterns determine a circle?
- a pattern that cancels each other out
`GGLLGG` means move forward twice, the two `L` faces backwards and essentially negates the steps.



Needed to do a bit of research for this question.

Trajectory Attractor
- trajectories where a system evolves too. Would the path diverse or limited.
- limited essentially means that the trajectory does not leave circle
Limit Cycle Trajectory
- a limit trajectory cycle will return to start after at most 4 cycles. That is because it has 4 directions to go to.

- if after one cycle, the robot isn't facing north then after 4 cycles the robot will return to a cirle



## Code

``` python
class Solution:
    def isRobotBounded(self, instructions: str) -> bool:

        # forward right down left
        directions = [[0, 1], [1, 0], [0, -1], [-1, 0]]

        pos = [0, 0]

        facing = 0

        for i in instructions:
            if i == "L":
                facing = (facing - 1) % 4
            elif i == "R":
                facing = (facing + 1) % 4
            else:
                pos[0] += directions[facing][0]
                pos[1] += directions[facing][1]

        return pos == [0, 0] or facing != 0
```

## Runtime/Memory
Time: O(n) n being the length of the string instruction since we iterate through each character to move the robot

Memory: O(1) The two variables created are constant space