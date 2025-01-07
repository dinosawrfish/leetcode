## Approach
I need to return the odd count of integers given the lower and higher limit of that range.

The limits need to be included in the count.

My initial thoughts is to do simple addition starting at the lower limit and once the higher limit is reached (checked by a while loop) we can stop the pattern and return the count of the odd numbers added. That can take too much time though depending on how big the range is

We can calculate the number of odd numbers by subtracting high and low and dividing by 2.

for even numbers
`(high - low + 1) // 2`

for odd numbers
`(high - low) // 2 + 1`

## Code
``` python
def countOdds(self, low: int, high: int) -> int:


        if low % 2 == 0:
            return (high - low + 1) // 2
        return (high - low) // 2 + 1
```

## Time/Space Complexity
Time: O(1)
Space: O(1)