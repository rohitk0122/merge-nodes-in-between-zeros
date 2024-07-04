# merge-nodes-in-between-zeros
class Solution {
    public ListNode mergeNodes(ListNode head) {
       ListNode dummy = new ListNode(0);  // Dummy node to simplify edge cases
        ListNode current = dummy;
        ListNode node = head.next;  // Skip the initial 0
        int sum = 0;

        while (node != null) {
            if (node.val == 0) {
                if (sum != 0) {
                    current.next = new ListNode(sum);
                    current = current.next;
                    sum = 0;
                }
            } else {
                sum += node.val;
            }
            node = node.next;
        }
        
        return dummy.next;  // Return the next node of dummy as the new head
    }
}

class Main {
    // Helper function to create a linked list from an array
    public static ListNode createLinkedList(int[] arr) {
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;
        for (int value : arr) {
            current.next = new ListNode(value);
            current = current.next;
        }
        return dummy.next;
    }

    // Helper function to print the linked list
    public static void printLinkedList(ListNode head) {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.val + " ");
            current = current.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        // Example usage
        Solution solution = new Solution();
        int[] input = {0, 1, 2, 0, 3, 4, 0};
        ListNode head = createLinkedList(input);
        ListNode modifiedHead = solution.mergeNodes(head);
        printLinkedList(modifiedHead);  // Output should be: 3 7 
 
    }
}
