
# Add Two Numbers - Linked List Solution

## Problem Description

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Example

```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807
```

## Solution

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummyNode = new ListNode();
        ListNode curr = dummyNode;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;
            
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            
            carry = sum / 10;
            curr.next = new ListNode(sum % 10);
            curr = curr.next;
        }

        return dummyNode.next;
    }
}
```

## Algorithm Explanation

1. Create a dummy head node to simplify the linked list construction
2. Initialize a pointer to the current node, starting at the dummy node
3. Track a carry value (initially 0)
4. Iterate through both linked lists simultaneously until both lists are exhausted and there's no remaining carry
   - Add the current carry to the sum
   - If there's a valid node in the first list, add its value to the sum and move to the next node
   - If there's a valid node in the second list, add its value to the sum and move to the next node
   - Calculate the new carry (sum divided by 10)
   - Create a new node with the digit value (sum modulo 10)
   - Move the current pointer to this new node
5. Return the next node after the dummy head, which is the start of the result list

## Complexity Analysis

- **Time Complexity**: O(max(m, n)) where m and n are the lengths of the two linked lists
- **Space Complexity**: O(max(m, n)) for the output linked list

## Notes

- This solution handles lists of different lengths
- The while loop continues until both lists are processed AND any final carry is handled
- Using the dummy head node pattern simplifies edge cases and eliminates the need for special handling of the first node
