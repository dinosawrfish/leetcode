# Solution 1
## Approach

My first thought on converting a string to lowercase is using Python's built in function
`lower()`

## Code

``` python
def toLowerCase(self, s: str) -> str:
        return s.lower()
```

## Runtime/Memory

Runtime: O(n) n being the length of string since lower has to go through all chars in string
Memory: O(1) nothing was created in memory

# Solution 2
## Approach

What if we want to implement our own function to make all uppercase chars to lowercase in a given string?

I would need to look at each char in a string and change the char only if the char is upper case. I can create a dictionary with the upper chars as keys and their corresponding lower case char as values.

We can ignore any chars that are non upper chars.

## Code

``` python
def toLowerCase(self, s: str) -> str:

        upper_to_lower_dict = {
            'A': 'a',
            'B': 'b',
            'C': 'c',
            'D': 'd',
            'E': 'e',
            'F': 'f',
            'G': 'g',
            'H': 'h',
            'I': 'i',
            'J': 'j',
            'K': 'k',
            'L': 'l',
            'M': 'm',
            'N': 'n',
            'O': 'o',
            'P': 'p',
            'Q': 'q',
            'R': 'r',
            'S': 's',
            'T': 't',
            'U': 'u',
            'V': 'v',
            'W': 'w',
            'X': 'x',
            'Y': 'y',
            'Z': 'z'
        }

        lower_word = ""
        for char in s:
            if char in upper_to_lower_dict:
                char = upper_to_lower_dict[char]
            lower_word += char

        return lower_word

```

## Runtime/Memory

Runtime: O(n) n being the length of string since lower has to go through all chars in string
Memory: O(1) dict and new word are constant space

# Solution 3
## Approach

My attempt at reproducing lower function.

I need to take advantage of the ASCII code.

`A lower letter is equal to the ascii code of upper letter plus 2^5 or 32`


## Code

``` python
def toLowerCase(self, s: str) -> str:

    lower_word = ""
    for char in s:
        if 'A' <= char <= 'Z':
            char = chr(ord(char) + 32)
        lower_word += char

    return lower_word

```

## Runtime/Memory

Runtime: O(n) n being the length of string since lower has to go through all chars in string
Memory: O(1) new word is constant space