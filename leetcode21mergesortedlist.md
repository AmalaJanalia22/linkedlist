/**
 * Problem: Merge Two Sorted Linked Lists
 * Given two sorted linked lists, merge them into a single sorted linked list.
 * 
 * Approach:
 * 1. Use a dummy node to simplify the merge process.
 * 2. Compare nodes from both lists and attach the smaller one.
 * 3. Attach the remaining nodes after one list is exhausted.
 * 
 * Time Complexity: O(N + M)
 * Space Complexity: O(1)
 */

class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(-1); // Dummy node to simplify merging
        ListNode current = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
                current.next = list1;
                list1 = list1.next;
            } else {
                current.next = list2;
                list2 = list2.next;
            }
            current = current.next; // Move the pointer forward
        }

        // Attach the remaining nodes
        current.next = (list1 != null) ? list1 : list2;

        return dummy.next; // Return the head of the merged list
    }
}
