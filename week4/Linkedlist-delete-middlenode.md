


# DELETE MIDDLE NODE IN A LINKEDLIST

[LEETCODE](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/submissions/1357189469/)



### Time Complexity

The time complexity of the `deleteMiddle` function is `O(n)`, where `n` is the number of nodes in the linked list. This is because the function iterates through the linked list with the `high` pointer moving at twice the speed of the `low` pointer, so the traversal of the list occurs in linear time.

### Space Complexity

The space complexity of the `deleteMiddle` function is `O(1)`, which means it uses constant space. The function only uses a few pointers (`low`, `high`, `prev`, `temp`, and `next`), regardless of the size of the input linked list.



```python


# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteMiddle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head is None or head.next is None:
            return None


        low=high=head
        prev=None
        temp=head
        next=0
        while high and high.next:
            prev=low
            low=low.next
            high=high.next.next
        
        if prev:
            prev.next=low.next
        return head
        


```


## Approach to Delete Middle Node of a Singly-Linked List

1. **Edge Case Handling:**
   - If the list is empty (`head` is `None`) or contains only one node (`head.next` is `None`), return `None` as there is no middle node to delete.

2. **Initialize Pointers:**
   - Use two pointers, `low` and `high`, both initialized to the `head` of the list.
   - Maintain a `prev` pointer to keep track of the node before `low`.

3. **Traverse the List:**
   - Move `high` pointer two steps at a time (i.e., `high = high.next.next`).
   - Move `low` pointer one step at a time (i.e., `low = low.next`).
   - Update `prev` to be the node before `low` (i.e., `prev = low`).

4. **Delete the Middle Node:**
   - When `high` reaches the end of the list, `low` will be pointing to the middle node.
   - Update the `next` pointer of `prev` to skip the middle node (`prev.next = low.next`).

5. **Return Modified List:**
   - Return the head of the modified list.

### Python Code

```python
class Solution:
    def deleteMiddle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head is None or head.next is None:
            return None

        low = high = head
        prev = None

        while high and high.next:
            prev = low
            low = low.next
            high = high.next.next
        
        if prev:
            prev.next = low.next

        return head

