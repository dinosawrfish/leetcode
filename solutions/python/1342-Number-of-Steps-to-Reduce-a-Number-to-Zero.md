## Approach

Get the number of steps of reducing a given number to zero with rules
if even then divide by 2
if odd subtract by one

Simulated the rules with a while statement until the number reduced to zero

## Code

``` python
class Solution:
    def numberOfSteps(self, num: int) -> int:
        steps = 0
        while num > 0:
            if num % 2 == 0:
                num = num/2
            else:
                num -= 1
            steps += 1

        return steps

```

## Runtime/Memory

Runtime: O(logn) since at each iteration the number is reduced by half so steps reduced by half

Memory: **steps** is constant