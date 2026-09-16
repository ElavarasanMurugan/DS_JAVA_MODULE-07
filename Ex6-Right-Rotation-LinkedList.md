# Ex6 Right Rotation LinkedList
## DATE: 16-09-2026
## AIM:
To write a Java  program to: Create a singly linked list.Rotate the linked list to the right by k positions.Display the rotated linked list.

## Algorithm
1. Create a singly linked list and insert the given elements at the end.
2. Read the value of k, which represents the number of right rotations.
3. Find the length of the linked list and the last node.
4. Calculate k = k % length to handle rotations greater than the list size.
5. Find the node at position length - k and make it the new head.
6. Connect the old last node to the old head.
7. Break the link before the new head to complete the rotation.
8. Display the rotated linked list.

## Program:
```
/*
Program to  Right Rotation LinkedList
Developed by:Elavarasan M 
RegisterNumber: 212224040083  
*/
```

```java
import java.util.*;

public class RotateLinkedList {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    static Node insert(Node head, int data) {

        Node newNode = new Node(data);

        if (head == null) {
            return newNode;
        }

        Node temp = head;

        while (temp.next != null) {
            temp = temp.next;
        }

        temp.next = newNode;

        return head;
    }

    static Node rotateRight(Node head, int k) {

        if (head == null || head.next == null || k == 0) {
            return head;
        }

        // Find length and last node
        int length = 1;
        Node last = head;

        while (last.next != null) {
            last = last.next;
            length++;
        }

        // Avoid unnecessary rotations
        k = k % length;

        if (k == 0) {
            return head;
        }

        // Make the list circular
        last.next = head;

        // Find new last node
        int steps = length - k;
        Node newLast = head;

        for (int i = 1; i < steps; i++) {
            newLast = newLast.next;
        }

        // Set new head
        Node newHead = newLast.next;

        // Break the circular link
        newLast.next = null;

        return newHead;
    }

    static void display(Node head) {

        Node temp = head;

        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        Node head = null;

        for (int i = 0; i < n; i++) {
            int data = sc.nextInt();
            head = insert(head, data);
        }

        int k = sc.nextInt();

        head = rotateRight(head, k);

        System.out.println("Rotated Linked List:");
        display(head);
    }
}
```
## Output:

![alt text](screenshots/image-1.png)

## Result:
Thus, the Java program to perfom right rotation on linked list is implemented successfully.
