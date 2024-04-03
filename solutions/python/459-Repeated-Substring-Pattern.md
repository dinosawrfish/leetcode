## Approach

First thing that comes to mind are rotations.

Given a string `s` a rotation can be checked by `wheel = s + s`.

`abab abababab`

`aba abaaba`

If `s` has more than one pattern then that pattern repeated twice fold and could be seen between the first and second rotation. The string should be found again in the middle of the wheel.

Not all tests passed with that mindsest since it missed passing cases in which checking at the middle did not give the original string since the pattern was missed.

`abababab` `ababababababab` middle would be `babababa` so out of frame to `ab` pattern.

How is a pattern defined.
`wheel = s + s`
We need to confirm if s in a repeated pattern
`s = p*k` p being the pattern substring and k the number of times it is repeated
`wheel = 2(pk)`
for s to have a pattern `k > 1` that is what I need to prove.

I need to redefine `wheel`.

If the string is patterned I can shift the rotation and check if I can find a pattern within the wheel.

Still hard to understand but can remove first and last character in wheel to prove pattern.

`wheel = s1 + s2` `s1 = s[1:]` `s2 = s[:-1]`

`wheel = (s1 + p*(k-1)) + (p*(k-1) + tail)`
if k = 1, no pattern
`wheel = s1 + s2` which fails because s = p so no pattern

if k > 1,
`wheel = s1 + p(2k-2) + s2`
`2k-2 = x` x being the number of times `p` occurs
so to have `s = p*k` `x >= k`
`2k-2 >= k -> k >= 2` which is equivalent ot `k > 1`


A wheel made of a string that already has patterns and to avoid missfraiming we can get rid of the first and last character of the wheel and confirm if the pattern is observed to confirm rotation.

## Code

``` python
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:

        wheel = s + s

        if s in wheel[1:-1]:
            return True

        return False
```

## Runtime/Memory

runtime: O(n) concatenation of string s in python takes O(n) times, checking if s in wheel also takes O(n) times

memory: O(n) since creating wheel concatenates two strings with length n so O(2n) -> O(n)


#TODO: write divisor solution

## Approach

My first thought was to create a list of all the possible substrings and return true if any of them can be assembled to the string `s`.

While this passed the test, runtime was slower than most submissions so I tried to find a way to not need to check evey possible substring each time and assemble them.

Goal: reduce runtime

An acceptable substring that can be the pattern needs its length to be completely divisible by the length of `s`.

The largest a substring can be to be repeated at least one is half the size of `s`.

if `p*k = s` p being the pattern substring and k the number the times p is repeated then for at least `k > 1`
`s/p > 1` or `s > p` and if `k=2` then `2p = s` or `p = s/2`

I can iterate through half the characters in `s`, check that the substring length is divisible by `s` and check if the pattern times the expected `k` is equal to `s`. Return False otherwise

## Code

``` python
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:

        for index in range(1, len(s)//2 + 1):
            if len(s) % index == 0:
                pattern = s[:index]
                if s == pattern * (len(s) // index):
                    return True

        return False
```

## Runtime/Memory

Runtime: O(n*sqrt(n)) There are two things the functions is doing. It is iterating through half the list so n/2 -> n removing the constant and within each iteration, the pattern is assembled with divisor which a string can have 2 * sqrt(n) divisors.

Memory: O(n) concatenates pattern using up to n/2 length of `s`