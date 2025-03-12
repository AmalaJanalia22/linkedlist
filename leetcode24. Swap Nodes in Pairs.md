Swap Nodes in Pairs - Linked List Operation

## Description:
An efficient Java solution to swap adjacent nodes in a linked list without changing node values.

## Problem Description

Given a linked list, swap every two adjacent nodes and return its head. The solution must:
- Swap the nodes by changing the links/pointers, not by swapping the values
- Handle edge cases (empty list, single node)
- Maintain the original structure for remaining nodes if there's an odd number of nodes

## Example

**Input:** 1->2->3->4  
**Output:** 2->1->4->3

**Input:** 1->2->3  
**Output:** 2->1->3

## Time and Space Complexity

- **Time Complexity:** O(n) - where n is the number of nodes in the linked list
- **Space Complexity:** O(1) - only constant extra space is used

## Implementation Details

The algorithm uses a dummy node approach to simplify handling the head of the list. It maintains a pointer that traverses the list, swapping each pair of nodes by rearranging their connections.

Key steps in the solution:
1. Create a dummy node that points to the head
2. Traverse the list, swapping adjacent nodes by rearranging pointers
3. Return the new head of the list (dummy.next)

## Code

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode point = dummy;
        while(point.next != null && point.next.next != null) {
            ListNode swap1 = point.next;
            ListNode swap2 = point.next.next;

            swap1.next = swap2.next;
            swap2.next = swap1;

            point.next = swap2;

            point = swap1;
        }
        return dummy.next;
    }
}
```
