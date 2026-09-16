# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE: 16-09-2026
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1. Start the program.
2. Create a `Node` class to represent each node in the linked list, containing:

   * `data` → stores the value of the node.
   * `next` → stores the reference to the next node.
3. Create a `RemoveSpecificValue` class to manage linked list operations.
4. Insert elements into the linked list using the `insert()` method.
5. Read the integer `val`, which is the value to be removed, from the user.
6. Remove the nodes containing the target value:

   1. Handle the case where the head node(s) contain `val`.
   2. Traverse the list using a temporary pointer.
   3. If the next node contains `val`, unlink it by changing the current node's `next` reference.
7. Display the modified linked list.
8. Stop the program.


## Program:
```
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: Elavarasan M
RegisterNumber: 212224040083 
*/
```

```java
import java.util.*;

class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
    }
}

class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode dummy=new ListNode(-1);
        dummy.next=head;
        ListNode prev=dummy;
        ListNode curr=head;
        while(curr!=null){
            if(curr.val==val){
                prev.next=curr.next;
            }
            else{
                prev=curr;
            }
            curr=curr.next;
        }
        return dummy.next;
        
    }
}

public class Main {

    public static ListNode buildList(int[] arr) {
        if (arr.length == 0) return null;
        ListNode head = new ListNode(arr[0]);
        ListNode current = head;
        for (int i = 1; i < arr.length; i++) {
            current.next = new ListNode(arr[i]);
            current = current.next;
        }
        return head;
    }

    public static String listToString(ListNode head) {
        List<Integer> result = new ArrayList<>();
        while (head != null) {
            result.add(head.val);
            head = head.next;
        }
        return result.toString(); 
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

     
        String input = scanner.nextLine().replaceAll("\\s", "");
        int[] nums = Arrays.stream(input.split(",")).mapToInt(Integer::parseInt).toArray();

       
       
        int val = scanner.nextInt();

        ListNode head = buildList(nums);
        Solution solution = new Solution();
        ListNode updated = solution.removeElements(head, val);

        System.out.println(listToString(updated));

        scanner.close();
    }
}
```
## Output:

![alt text](screenshots/image-2.png)

## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
