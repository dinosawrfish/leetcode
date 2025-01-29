## Approach

Given a singly linked list, I need to return the reversed list.

I can recursively go down the list, and set its link to the previous value.

My base case is when we reach the end of the list of when head.next is None or when the list of empty.

Once we reached the end of the line, we set its head at the end, and remove the original path

1 -> 2 -> 3 -> 4 -> 5 -> 4
5 -> 4 <- 3 <- 2 <-1

then return that head
5 -> 4 <- 3 <- 2 <-1
3 -> 4 -> 3
5 -> 4 -> 3 <- 2 <- 1

2 -> 3 -> 2

5 -> 4 -> 3 -> 2 <- 1

1 -> 2 -> 3
5 -> 4 -> 3 -> 2 -> 1

## Code
``` python
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:

        if head is None or head.next is None:
            return head

        h2 = self.reverseList(head.next)
        head.next.next = head
        hed.next = None
        return h2
```

## Time/Space Complexity

Runtime: O(n) n being the length of the linked list since the recursion is visiting every node

Memory: O(n) the depth of the recursion is the number of nodes in the linked list.


## Iterative solution to study later
``` python
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:

        prev = None
        curr = head
        while curr:
            temp_next = curr.next
            curr.next = prev
            prev = curr
            curr = temp_next

        return prev
```