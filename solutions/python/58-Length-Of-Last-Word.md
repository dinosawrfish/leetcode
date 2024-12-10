# Solution 1
## Approach
First thought would be to first identity if the string is empty or is all non characters.

Then use the split built in function to get a list of all char words since the default delimiter is spaces. Simply return the last item in the list after.

## Code

``` python
 def lengthOfLastWord(self, s: str) -> int:
        if not s or s.isspace():
            return 0
        else:
            word_list = s.split()
            return len(word_list[-1])
```

## Runtime/Memory

Runtime: O(n) n being the length of `s` since split scans whole string to output the list
Memory: O(n) split returns a list of substrings that needs to be stored.


# Solution 2
## Approach
I would like to find a solution that does not require to take O(n) of space.

Instead of storing a list of words, I can identify where the last word ends, and count back until a space is identified.

I would start counting the length of the last word when the first non space char hits and stop counting when a space hits.

The only time this would break is when the string has no spaces, then I will need to stop when the whole string is traversed.

## Code

``` python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        word_length = 0
        s_length = len(s)

        while s_length > 0:
            s_length -= 1

            if s[s_length] !=" ":
                word_length += 1
            elif word_length > 0:
                break

        return word_length
```

## Runtime/Memory

Runtime: O(n) n being the length of `s` since the while loop can trace all the chars in the string
Memory: O(1) Nothing being added to memory other than constant variables.