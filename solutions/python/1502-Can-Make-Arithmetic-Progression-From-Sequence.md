## Approach

Arithmetic progression happens where a sequence has the same difference per step.

An array with all the same numbers is an arithmetic progression.

An array in which its average is equal to the arithmetic diff times the length of the array.

avg = sum of array / length of the array

`sum of array = avg/length of array`
`sum of array = diff * length of array`
`diff * length of array = avg / length of array`
`diff = avg`


To check if an array of numbers can be rearranged to make an arithmetic progression, we can rearrange each number in the array if the the differnce between the min number in the array and the current number is divisible by the difference.

Need to return false if it isn't divisble or if there are multiple but not all numbers in the list that are the same

## Code

``` python
class Solution:
    def canMakeArithmeticProgression(self, arr: List[int]) -> bool:

        min_num = min(arr)
        max_num = max(arr)
        arr_len = len(arr)

        if max_num - min_num == 0:
            return True

        if (max_num - min_num) % (arr_len-1):
            return False

        diff = (max_num-min_num)//(arr_len-1)
        index = 0
        while index < arr_len:
            if (arr[index] - min_num) % diff:
                return False
            j = (arr[index] - min_num) // diff
            if index == j:
                index += 1
                continue
            if arr[index] == arr[j]:
                return False

            arr[index], arr[j] = arr[j], arr[index]

        return True

```

## Runtime/Memory

Runtime: O(n) worst case we check every value in the list, finding min and max is also O(n)

Memory: O(1) modified existing array