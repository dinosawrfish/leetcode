## Approach

Check if two strings are rotations of each other. We can think of a rotated string as a wheel that can be turned multiple times.

`s = 'abc'` can rotate twice to `s2 = abcabc`

The farthest rotation of `s` is two shifts `t = cab` which is a substring of `s2`.

So to confirm if a string `t` is a rotation of `s` then we can make a 2 rotation wheel of `s` and check if `t` is in.

Essentially a 2 rotation wheel will have all possible rotation shifts in the string.

## Code

``` python
class Solution:
    def rotateString(self, s: str, goal: str) -> bool:

        if len(s) != len(goal):
            return False

        rotate_twice = s + s

        return goal in rotate_twice

```

## Runtime/Memory

Runtime: O(n^2) where n is the length of string s since the function is concatinating a new string

Memory: O(n) n being the length of of **rotate_twice** created