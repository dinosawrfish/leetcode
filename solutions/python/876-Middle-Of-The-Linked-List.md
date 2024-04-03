## Approach

To traverse through a path we can do a rabbit/turtle pointers.

Essentially a pointer that travels twice as fast a slower pointer.

Since the fast pointer is twice faster, by the time the pointer reaches the end the slower pointer should be halfway across the path so return the slower pointer.

## Code

``` python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:

        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        return slow

```

## Runtime/Memory

Runtime: O(n) n being the length of the linked list

Memory: O(1) rabbit/turtle pointers are just O(1) each