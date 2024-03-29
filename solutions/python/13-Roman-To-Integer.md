### Approach

To convert a roman numeral to integer we would first need a dictionary/hashmap of the roman symbols to integers.

We can iterate per character in the string and get the associated integer and calculate the sums per character. Each iteration of roman symbol should represent a smaller digit

Need to consider roman numeral rules:
- When a roman symbol represents a smaller integer than the symbol to its right, both those symbols represent an integer that is the is the difference between the right symbol to the left symbol

`IV = 4` can be seen as `5 (V) - 1 (I) = IV 4`

### Code

``` python
class Solution:
    def romanToInt(self, s: str) -> int:
        r_dict = {
            "I": 1,
            "V": 5,
            "X": 10,
            "L": 50,
            "C": 100,
            "D": 500,
            "M": 1000
        }

        answer = 0
        index = 0

        while index < len(s):

            if index + 1 < len(s) and r_dict[s[index]] < r_dict[s[index + 1]]:
                answer += r_dict[s[index + 1]] - r_dict[s[index]]
                index += 2

            else:
                answer += r_dict[s[index]]
                index += 1

        return answer
```


### Runtime/Memory

Time Complexity: **O(1) since s can only contain a set of roman symbols that can make a number up to 3999, the time complexity is a constant. If there were an arbirtary number of symbols then O(n) n being the length of the roman numeral.

Space Complexity: **O(1) all created variables are constants