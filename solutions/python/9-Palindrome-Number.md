*good to review*

## Approach

We would first think what is a palindrome and what is not a palindrome.

What it is:
- a set of characters that can be read the same if reversed
- a palindromic integer needs to be a positive integer
- can imagine if length folded like a book, each side would mirror

What it is not:
- an integer of base 10, since moving the rightmost zero to the left is equivalent to losing the digit.
- a negative integer since the negative sign cannot be carried to the right when reversed

The easiest approach is to convert the integer to string then check if the reversed string is equal to the original.

But, we want to keep the data type as an integer.

- To reverse an integer would be to change the position of the digits. For example, given a 3 digit number, the digit at the ones position would be moved to the hundreds, the dig in the tens would stay at the tens, and the digt at the hundreds would go to the ones.

- It would be easier to sum from the bigger digit to the smaller digit.

- Since a palindrome is mirrored, only half the length of the reversed need to be build

We can grab the digit in ascending order (ones, then tens, then hundreds, etc) by getting the remainder of the given integer.

To move up a digit would be to multiple the digit by 10.

Each iteration of grabbing the first digit from the given integer needs to be removed to grab the next

How to iterate digit placement? Can't for loop a int, range won't help, so conditional

A palindrome will be equal to the reversed.
`242 == 242`
`242 > 0`
`24 > 2`
`2 < 24` Change !

`1221` == `1221`
`1221` > `0`
`122` > `1`
`12` = `12`Change !

If not a palindrome:
`241 > 142`
`241 > 0`
`24 > 1`
`2 < 14` Change !

`243 < 342`
`243 > 0`
`24 > 3`
`2 < 34` Change!

Iteration can stop when the calculated reversed is not less than the original number.

A palindrome exist when half of the reversed integer is equal to the remainder of the original integer (this is when the length is even so a perfect mirror)

Or when the length of digits is odd, the middle number does not matter so a palindrome is when the remainder of the original integer is equal to the ten's place of the reversed number. (Kind of a book with a wedge in the middle).

## Code

``` Python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0 or (x % 10 == 0 and x != 0):
            return False

        reverted_num = 0
        while x > reverted_num:
            reverted_num = (reverted_num * 10) + (x % 10)
            x //= 10
        return reverted_num == x or x == reverted_num//10
```

## Runtime/Memory

Time Complexity: *O(n)*
The function iterates ntimes, n being the number of digits in the given integer and since only half the digits are reversed n/2 iterations happen. Removing the constant will leave to n.

Space Complexity *O(1)
**reverted_num** only stores an int so constant space