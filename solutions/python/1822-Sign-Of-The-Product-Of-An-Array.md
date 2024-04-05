## Approach

Return 1 if the product of the array is pos and -1 if neg.

We can create a variable with 1 and then iterate through the array. If any number in the array is zero then the whole product return zero.

The sign of a product changes if a multiple is a negative number. Multiply by -1 if number in the array is negative

Return the sign after iterations

## Code

``` python

class Solution:
    def arraySign(self, nums: List[int]) -> int:

        sign = 1
        for num in nums:
            if num == 0:
                return 0
            if num < 0:
                sign = -1 * sign

        return sign

```

## Runtime/Memory

Runtime: O(n) the function iterates each number in the array

Memory: O(1) **sign** stores an integer at constant space.