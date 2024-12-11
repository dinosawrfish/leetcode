## Approach
I need to keep track of the score and based on the operations given in the operations list.

I will need to create an empty list to keep the score.

I will need to iterate through operations list to apply operations.

Once the iteration is done, I sum all the scores in the score list and return the sum.

## Code

``` python
   def calPoints(self, operations: List[str]) -> int:

        scores = []

        for op in operations:
            try:
                scores.append(int(op))
            except:
                if op == 'C' and len(scores):
                    scores.pop()
                elif op == '+' and len(scores) > 1:
                    scores.append(scores[-1] + scores[-2])
                elif op =='D' and len(scores):
                    scores.append(scores[-1] * 2)

        score_sum = 0
        for score in scores:
            score_sum += score

        return score_sum
```

## Runtime/Memory

Runtime: O(n) have to iterate through each operation in list
Memory: O(1) record scores by each operation on list