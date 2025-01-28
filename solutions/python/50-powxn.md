## Approach
I need to implement `pow(x,n)` which calculates `x^n`

For example,
x = 2 n = 10
2^10 = 1024

x = 2 n = -2
2 ^-2 = 1/2^2 = 1/4 = .25

Part of me just wants to write
`return x**n`.
But I think that may be too lazy...

If asked to be less lazy I need to figure out how to implements powers.

What is a power?
Multiply x by n times
so 2^10 = 2*2*2*2*2*2*2*2*2*2 = 1024

So I can iterate a multiplication or even do a recursion.

```
ans = 1 // since x^0 is always 1 base case

if pos int -> multiplier = x
if neg int -> multiplier = 1/x


for i in range(n)

    4 = multiplier*2
    8 = multiplier*4
    16=multiplier*8
    ....
    1024=multiplier*512

```
This method is not the best since runtime is O(n) which can significantly slow down the equation.

I can also cut down the runtime to O(n/2) by only iterating to half since 2^10 = 2^5 * 2^5.
```
ans = 1 // since x^0 is always 1 base case

if pos int -> multiplier = x
if neg int -> multiplier = 1/x


for i in range(n)

    4 = multiplier*2
    8 = multiplier*4
    16=multiplier*8
    ....
    1024=multiplier*512

if n odd -> return ans*ans*multiplier
if n even -> return ans*ans
```

We can try a recursive method to cut down runtime to O(logn)

The base cases for the recursion is when
n = 1 -> return x
n = 0 -> return 1

we still need to define the multiplier depending whether n is pos/neg.
``` python
    def myPow(self, x: float, n: int) -> float:

        if n == 0:
            return 1
        elif n < 0:
            return 1 / self.myPow(x, -n)

        return x * self.myPow(x,n-1)
```

While this is the basic recursion the runtime is not log(n)

Binary Exponentation
- repeatedly square x and halve n

x^2 * 1^n/2 if even
x * x^2 * 1^(n-1)/2 if odd

## Code
``` python
class Solution:
    def binaryExp(self, x: float, n: int) -> float:

        if n == 0:
            return 1

        if n < 0:
            return 1.0 / self.myPow(x, -1 * n)

        if n % 2 == 1:
            return x * self.myPow(x*x, (n-1)//2)
        else:
            return self.myPow(x*x, n // 2)

    def myPow(self, x: float, n: int) -> float:
        return self.binaryExp(x,n)
```


## Runtime/Space Complexity
Runtime: O(logn) run time for binary exp

Memory: O(logn) memory call for recursions
