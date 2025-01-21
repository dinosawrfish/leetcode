## Approach
Return the sum of two binary strings.

Adding in binary in base 2.

I only need to care about carry overs if the total addition is two or bigger.

I can iterate through both strings in reverse and convert that char to int and do the addition. if the addition is two or more then we have to carry over 1 to the next addition.

## Code
``` python
def addBinary(self, a: str, b: str) -> str:

        carry = 0
        n = max(len(a), len(b))
        a, b = a.zfill(n), b.zfill(n)
        ans = []

        for i in range(n - 1, -1, -1):
            if a[i] == "1":
                carry += 1
            if b[i]== "1":
                carry += 1

            if carry % 2 == 1:
                ans.append("1")
            else:
                ans.append("0")

            carry //=2

        if carry == 1:
            ans.append("1")
        ans.reverse()

        return "".join(ans)
```

## Time/Space Complexity
Runtime: O(n) n being the length of the longer string
Space: O(n) n being the length of the longer string when the summation is built