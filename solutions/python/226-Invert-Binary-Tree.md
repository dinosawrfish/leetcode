## Approach

To invert a binary tree given root, can transverse recursively left most first then right most and switch each node.

Return recursive function when there is no root to invert

## Code

``` python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return root

        self.invertTree(root.left)
        self.invertTree(root.right)
        root.left, root.right = root.right, root.left

        return root
```

## Runtime/Memory

Runtime: O(n) N being the number of nodes in the tree since the function can be run per node

Memory: O(n) the function is being called recursively so will return per node so n times