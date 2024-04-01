## Approach

Given an array of digits that represents a large integer, to return an array that is plus one, two scenerios happen:

- if the rightmost digit is 9, that digit becomes one and the second rightmost digit needs to be added by one
- else, increment the rightmost digit by 1

the only exception is an empty list which should just return an array with 1.

## Code

``` python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:

        if not digits:
            return [1]

        if (digits[-1] + 1) == 10:
            answer = self.plusOne(digits[:-1])
            answer.append(0)
        else:
            digits[-1] = digits[-1] + 1
            answer = digits

        return answer
```

## Runtime/Memory

Runtime: O(n) Worst case scenario each digit needs to be incremented by one n amount of times n being the length of the array
Memory: O(n) **answer** is an array with length n, n being the length of the original array