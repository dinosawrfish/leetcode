## Approach
Given an array of integers, I need to find their average excluding the min and max values in the array.

Do I need to traverse through the entire array?
Fow now, I am going to assume yes since I need to know what values to add up and compare to identify the min and max value.

I can keep track of the max and min value, and while traversing through the array, I add the values together and identify the max and min.

After traversal, I can subtract the min and max and then calculate the average.

## Code
``` python
    def average(self, salary: List[int]) -> float:

        min_val = salary[0]
        max_val = salary[0]
        total = 0

        for val in salary:
            total += val
            if val < min_val:
                min_val = val
            if val > max_val:
                max_val = val

        excluded_val = total - min_val - max_val

        excluded_range = len(salary) - 2
        avg = excluded_val/excluded_range
        return avg
```

## Time/Space Complexity
Time: O(n) n being the number of values in the given array since we are looping through the array.

Memory: O(1) created values are integers at constant space