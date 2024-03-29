## Approach

To find the substring in a string, we can first iterate the string per character.

For the substring to exist, the searched string needs to be the same length as the substring.

Per iteration, if the substring created from the index to the length of the desired substring is equal to the substring.

Return the index if so, return -1 if the substring wasn't found after iterations.



## Code

``` python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:

        for i in range(len(haystack) - len(needle) +1):
            if haystack[i : i+len(needle)] == needle:
                return i

        return -1
```

## Runtime/Memory

Runtime: O(n) the function is iterating n times, n being the length of the string.

Memory: O(1) since no new variables were made