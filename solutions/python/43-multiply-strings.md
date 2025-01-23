## Approach
Given two non neg integers in string, I need to return the product of both numbers.

I cannot convert the given strings to integers directly.

The next best thing I can think of using are the integer representation of the char's unicode.

Similarly to `67-add-binary` I can iterate over the strings in reverse, convert the char to unicode using `ord()`.

I will need to convert the unicode int to the actual integer.

0 -> 48
1 -> 49
2 -> 50
.
.
.
9 -> 57

so

`unicode - 48 = int`
48 - 48 = 0
49 - 48 = 1
50 - 48 = 2
.
.
.
57 - 48 = 9

Once I assemble the numbers I can do a multiplication to get the answer.

I need to know what place value the digit is for and multiply by ten to get it then add the number accordingly

```
num1 = "123"
num1_int = 0
length = 3

for i in range(3)
    place = 10^(length-1) //10^(3-1) -> 100
    char = num1[i] //"1"
    uni = ord(char) //49
    digit = uni - 48 //1
    add = digit * place // 1 * 100 -> 100
    num1_int += add //100
    length -= 1 //2

    place = 10^(1) //10
    char = numi1[1] //"2"
    uni = //50
    digit = 50 - 48 //2
    place = 2 * 10 //20
    num1_int += 100 + 20 //120
    length -=1 //1

    place = 10^0 //1
    char = "3"
    uni = 51
    digit = 51 - 48 //3
    place = 3 * 1 //3
    num1_int += 120 + 3 /123

//repeat for num2

return num1_int * num2_int
```

## Code
``` python
class Solution:
    def multiply(self, num1: str, num2: str) -> str:

        num1_int = 0
        num1_length = len(num1)
        num2_int = 0
        num2_length = len(num2)

        for i in range(num1_length):
            place = 10**(num1_length - i - 1)
            char = num1[i]
            uni = ord(char)
            digit = uni - 48
            addition = digit * place
            num1_int += addition

        for i in range(num2_length):
            place = 10**(num2_length - i - 1)
            char = num2[i]
            uni = ord(char)
            digit = uni - 48
            addition = digit * place
            num2_int += addition

        return str(num1_int * num2_int)
```


## Time/Space Complexity

Runtime: O(n) n being the largest length string since we are iterating through each character to convert to a digit

Space: O(1) all integers created are in constant space


### To study next time
``` python
def multiply(self, num1: str, num2: str) -> str:

        if num1 == "0" or num2 == "0":
            return "0"
        if num1 == "1":
            return num2
        if num2 == "1":
            return num1


        n1 = len(num1)
        n2 = len(num2)
        ans = [0] * (n1 + n2)
        digits1 = [int(d) for d in num1]
        for i in range(n2 - 1, -1, -1):
            digit2 = int(num2[i])
            for j in range(n1 - 1, -1, -1):
                k = i + j + 1
                carry = ans[k]
                digit = digit2 * digits1[j] + carry
                ans[k] = digit % 10
                ans[k - 1] += digit // 10

        if ans[0] == 0:
            return "".join(map(str, ans[1:]))
        return "".join(map(str,ans))
```