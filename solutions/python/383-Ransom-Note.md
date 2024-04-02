## Approach

To check if a string `m` can be created using the characters from another string `n`:
- length `n` >= length `m`
- all the characteds in `m` must exist in `n`

we can remove characters from `m` that are in `n` and return true if there are no remaining characters in `m`

to make sure a character in `n` is only chosen once, characters in `n` will be removed in order even if not in `m`. this helps know when `n`  is no good when ordered if the character is bigger than `m`.

We can iterate both strings while one runs out first.

## Code

``` python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:

        if len(ransomNote) > len(magazine):
            return False

        ransomNote = sorted(ransomNote, reverse=True)
        magazine = sorted(magazine, reverse=True)

        while ransomNote and magazine:

            if ransomNote[-1] == magazine[-1]:
                ransomNote.pop()
                magazine.pop()

            elif magazine[-1] < ransomNote[-1]:
                magazine.pop()
            else:
                return False

        return not ransomNote
```

## Runtime/Memory

runtime: O(nlog(n)) it takes nlogn time to sort a string. n time to go through the while  loop. n being the length of the largest string.

memory: O(1) the two sorted strings are constant