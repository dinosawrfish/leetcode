## Approach

  Given an array of ints, to move all zeros to end of array.

  Move all non zero ints to left most of array. This can be done by iterating array while storing a pointer incrementing the index to place the next non zero int.

  The last index the pointer has will always be the length of the array minus the number of non zero ints. That difference is the number of zeros in the list. We can iterate the array starting at the pointer to the end of the array to change the values to zero


## Code

``` python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """

        lastnonzero = 0

        for i in range(len(nums)):
            if nums[i] != 0:
                nums[lastnonzero] = nums[i]
                lastnonzero += 1

        for i in range(lastnonzero, len(nums)):
            nums[i] = 0
```

## Runtime/Memory

Runtime: O(n) the function iterated n amount of times first, n beign the length of the array and then iterated again with a sub length of the array so worst case scenario 2n iteration which without the constant is n times

Memory: O(1) **lastnonzero** is a int constant