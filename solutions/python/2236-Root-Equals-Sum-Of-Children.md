## Approach

Jaja, problems solved to figure out how to use LeetCode.

Given a binary tree with 3 nodes, we can return the bool of whether the root value is equal to the sum of its left and right child.


## Code

``` python

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def checkTree(self, root: Optional[TreeNode]) -> bool:
        return root.val == (root.left.val + root.right.val)

```

## Runtime/Memory

Runtime: O(1) summation takes O(1) bool check takes O(1) time

Memory: O(1) only using input variables and returning them takes O(1) space