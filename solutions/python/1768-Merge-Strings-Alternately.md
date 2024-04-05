## Approach

We need to to merge two strings into one and by alternating each character together.

We would first need to create an empty string to store the merged string.

The two given strings can have different lengths so iterate by the number of characters of the longest string

Per iteration check if the strings are long enough and if so add the character into the new string.

## Code

``` python

class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:

        new_word = ""
        max_length = max(len(word1), len(word2))
        for i in range(max_length):
            if i < len(word1):
                new_word += word1[i]
            if i < len(word2):
                new_word += word2[i]

        return new_word

```

## Runtime/Memory

Runtime: O(n) getting the max length between two strings takes O(n) and iterating through the max length takes O(n) n being the length of the longest string

Memory: O(1) the new string takes constant space