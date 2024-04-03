## Approach

we can modify the given array and increment by previous iteration to get the running sum.

## Code

``` python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        for i in range(1, len(nums)):
            nums[i] += nums[i-1]
        return nums

```

## Runtime/Memory

Runtime: O(n) the function iterates n times n being the length of array num

Memory: O(1) **nums** is being modified from given array