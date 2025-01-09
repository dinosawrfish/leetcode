## Approach
Given an integer array I need to return if possible the largest perimiter formed using three of the integers in the array.

There is a mathematical equation involved in this.

A perimeter of a triangle is the sum of the three lengths of a triangle.

a + b + c = P
a + b = P - c

P > c

Triangle Inequality: two sides of a triangle need to be larger or equal to than the third side or a + b >= c, b + c >= a, a + c >= b

I need to find the max perimeter so I can sort the array descending and check any three pairs.


## Code
``` python
    def largestPerimeter(self, nums: List[int]) -> int:

        sorted_nums = sorted(nums, reverse=True)

        for i in range(len(nums)-2):
            perimeter = sorted_nums[i] + sorted_nums[i+1] + sorted_nums[i+2]
            if sorted_nums[i] < sorted_nums[i+1] + sorted_nums[i+2]:
                return perimeter

        return 0
```

## Time/Space Complexity
Time: O(n*log(n)) since sorting an array
Space: O(n) creating the sorted array with n length of the given array