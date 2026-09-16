# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE: 16-09-2026
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm
1. Start the program.
2. Input an array `nums` representing a permutation of the numbers from `0` to `n - 1`.
3. Initialize a boolean array `visited[]` of size `n` to keep track of visited elements.
4. Initialize `maxLength = 0` to store the maximum length of any nested set.
5. For each index `i` in the array:

   1. If index `i` is not visited, start from index `i`.
   2. Keep following `nums[k]` until a visited element is encountered.
   3. Count the number of elements visited.
   4. Update `maxLength` if the current count is greater.
6. Output the value of `maxLength`.
7. End the program.

## Program:
```
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: Elavarasan M
RegisterNumber: 212224040083 
*/
```
```java
import java.util.*;
public class ArrayNestingMain {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine().trim();
        input = input.replace("nums =", "").replace("[", "").replace("]", "").trim();
        String[] parts = input.split(",");
        int[] nums = new int[parts.length];

        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution sol = new Solution();
        int result = sol.arrayNesting(nums);
        System.out.println(result);
        sc.close();
    }
}
class Solution {
    public int arrayNesting(int[] nums) {
        int maxlen = 0;
        boolean[] visited = new boolean[nums.length];
        for (int i = 0; i < nums.length; i++) {
            if (!visited[i]) {
                int count = 0;
                int curr = i;
                while (!visited[curr]) {
                    visited[curr] = true;
                    curr = nums[curr];
                    count++;
                }
                maxlen = Math.max(maxlen, count);
            }
        }
        return maxlen;

    }
}
```
## Output:

![alt text](screenshots/image-4.png)


## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
