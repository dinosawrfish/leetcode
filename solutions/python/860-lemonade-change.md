## Approach
Given an array of customers that their value represents their spending amount and will only buy one 5 dollar item, I need to return a boolean whether I am able to to give the right change to every customer. I do not start with any change myself.

I do not need to checkout every customer. As soon as I cannot provide change to one customer, I can return False.

I need to traverse through the array and calculate the customer's change. Then check my own change and determine if I have the right bills to pay back and update the remaining bills.

I will need to keep record how many 5, 10, 20 dollar bills I carry.

Return true if I can go through all the transactions, return false when I can't pay a change.

## Code
``` python
    def lemonadeChange(self, bills: List[int]) -> bool:

        cash_box = {
            5: 0,
            10: 0,
            20: 0
        }

        cost = 5

        for cust in bills:

            change = cust - cost
            cash_box[cust] += 1

            if change == 5:
                if cash_box[5]:
                    cash_box[5] -= 1
                else:
                    return False

            elif change == 15:
                if cash_box[10] and cash_box[5]:
                    cash_box[10] -= 1
                    cash_box[5] -= 1
                elif cash_box[5] >= 3:
                    cash_box[5] -= 3
                else:
                    return False

        return True
```

## Time/Space Complexity
Time: O(n) n being the length of the array.
Space: O(1) the dictionary created and change calculations are at constant space