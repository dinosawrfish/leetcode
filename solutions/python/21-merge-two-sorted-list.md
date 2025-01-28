## Approach
Merge two singly linked list to one sorted list.
The two lists are already sorted.

I should splice together the nodes of the two lists.

I need to return the head of the sorted list.

Things that come to mind are:

- sorting -> quick sort, bubble sort, merge sort

Merge Sort
- recursion sort
- base case an array with length 1 is sorted
- merge the returned arrays and sort them there


We can do a recursion sorting

The base case is when we go to the end of the linked list. and then compare the largest value
if l1 is None -> return l2
if l2 is none -> return l1

then check which head is smaller,
if l1 is smaller -> set its link by comparing the rest of l1 to l2
if l2 is smaller or equal -> set its link by comparing l1 to rest of l2


## Code

``` python

    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:

        if list1 is None:
            return list2
        elif list2 is None:
            return list1

        if list1.val < list2.val:
            list1.next = self.mergeTwoLists(list1.next, list2)
            return list1
        else:
            list2.next = self.mergeTwoLists(list1, list2.next)
            return list2

```


## Time/Space Complexity

Time Complexity: O(n + m) n and m being the lengths of both lists since the recursion has to visit every value to sort

Space Complexity: O(n + m) the recursion calls taken before returning