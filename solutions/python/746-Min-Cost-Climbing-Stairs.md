## Approach

This is like MSA! Use dynamic programing to create a bottom up.

make an empty list with length of the costs to store min cost path

then per each step add up the minimal price to the current steps price. The minimun prices should be added up the last two steps before the top of the floor.

## Code

``` python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:

        all_costs = [0] * len(cost)

        all_costs[0] = cost[0]
        all_costs[1] = cost[1]

        for i in range(2, len(cost)):
            all_costs[i] = cost[i] + min(all_costs[i-1], all_costs[i-2])

        return min(all_costs[len(cost)-1], all_costs[len(cost)-2])

```

## Runtime/Memory

Runtime: O(n) the function iterates through the length n of cost

Memory: **all_cost** is generated with length n, n being the length of array cost