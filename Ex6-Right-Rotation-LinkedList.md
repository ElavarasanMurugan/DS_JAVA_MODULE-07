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
import java.util.Scanner;

class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class prog {
    public static Node rotateRight(Node head, int k) {
        if (head == null || head.next == null || k == 0)
            return head;

        Node temp = head;
        int length = 1;
        while (temp.next != null) {
            temp = temp.next;
            length++;
        }

        temp.next = head;

        int stepsToNewHead = length - k % length;
        Node newTail = head;
        for (int i = 1; i < stepsToNewHead; i++) {
            newTail = newTail.next;
        }

        Node newHead = newTail.next;

        newTail.next = null;

        return newHead;
    }

    public static void printList(Node head) {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (n <= 0) {
            sc.close();
            return;
        }

        Node head = new Node(sc.nextInt());
        Node tail = head;
        for (int i = 1; i < n; i++) {
            tail.next = new Node(sc.nextInt());
            tail = tail.next;
        }

        int k = sc.nextInt();

        head = rotateRight(head, k);

        System.out.print("LinkedList: ");
        printList(head);

        sc.close();
    }
}
```
## Output:

![alt text](screenshots/image-1.png)

## Result:
Thus, the Java program to perfom right rotation on linked list is implemented successfully.
