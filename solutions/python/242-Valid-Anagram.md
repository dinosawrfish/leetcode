## Approach

An anagram is an equivalent combination of characters where order does not matter. What does matter is that both combinations have the same characters and its quantity.

Charactor to its quantity/frequency can be a dictionary/hashmap

Can create a counter dictionary per character.

To optimize can use 1 dictionary for both strings in questions.

This can be done by adding 1 for a character in string 1 and reduce by 1 for a character in string 2

If both strings are anagrams the count for all characters should zero out. Return false otherwise

## Code

``` python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:

        counter = defaultdict(int)

        for char in s:
            counter[char] += 1
        for char in t:
            counter[char] -= 1

        for val in counter.values():
            if 0 != val:
                return False

        return True
```

## Runtime/Memory

runtime: O(n) n being the length counter dictionary since function iterates how each val to be zero

memory: O(1)  key/val pairs will max to the constant number of unique characters