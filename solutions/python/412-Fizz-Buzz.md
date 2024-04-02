## Approach

We need to build an array with either the index (starting at 1) as a string, or
- `fizzbuzz` if div by 3 and 5
- `fizz` if div by 3
- `buzz` if div by 5

first create an empty array
iterate through the given integer `n` making sure starting at 1
check if iterating number meets requirements, if so append with appropiate string

## Code

``` python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        f_list = []
        for n in range(n):
            n = n+1
            if n%3 == 0 and n%5 == 0:
                f_list.append('FizzBuzz')
            elif n%3 == 0:
                f_list.append('Fizz')
            elif n%5 == 0:
                f_list.append('Buzz')
            else:
                f_list.append(str(n))

        return f_list
```

## Runtime/Memory

runtime: O(n) n being the given integer since the function iterates with the range of n

memory: O(n) **f_list** is an array that will have length n, n being the given integer since each iteration will append an item to the array