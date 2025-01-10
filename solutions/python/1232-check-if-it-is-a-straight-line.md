## Approach
Given a list of [x, y] coordinates i need to determine if they make a straight line.

A linear equation can be represented as

y = mx + b

y and x being a coordinate on the line, b being the point passing the y axis, and m being the slope the line is carried by.

I can take two points in the coordinate list to find the equation and then check if the equation is true under the rest of the coordinates.

Examples
[[1, 2], [2, 3], [3, 4]]

3 - 2 = m(2 - 1)
1 = m*1
m = 1
m = (y1 - y2)/ (x1 - x2)

For a vertical line this equation will break since you cannot divide by zero.

I am comparing slopes.

slope = y1 - y0 / x1 - xo

and I am comparing that to a calculated slope iterating through, i can keep the first point the same

calc_slope = yn - y0 / xn - x0

and I am checking if slope == calc_slope or
y1 - y0 / x1 - x0 = yn - y0 / xn - x0

to avoid the divisible by zero i can cross multiply

(y1 - y0)(xn - x0) = (yn - y0)(x1 - x0)

use this comparison instead


## Code
``` python
    def checkStraightLine(self, coordinates: List[List[int]]) -> bool:

        (x0, y0) = coordinates[0]
        (x1, y1) = coordinates[1]

        for i in range(2, len(coordinates)):
            x = coordinates[i][0]
            y = coordinates[i][1]
            if (y1 - y0)*(x - x0) != (y - y0)*(x1 - x0):
                return False
        return True
```

## Time/Space Complexity
Time: O(n) since we are traversing through the array
Space: O(1) constant space created