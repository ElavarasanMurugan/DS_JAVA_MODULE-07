# Flattening a Nested List Using an Iterator
## DATE: 16-09-2026
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm
1. Start the program.
2. Define a `NestedInteger` interface or class that can hold either:

   * A single integer.
   * A nested list of integers.
3. Create the `NestedIterator` class to flatten the nested list using a stack.
4. Implement the following methods:

   1. `hasNext()` → Checks whether more integers are available.
   2. `next()` → Returns the next integer in sequence.
5. In the main program:

   1. Create nested lists of integers.
   2. Create a `NestedIterator` object.
   3. Use the iterator to traverse and print all integers sequentially.
6. Stop the program.

## Program:
```
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: Elavarasan M
RegisterNumber: 212224040083 
*/
```

```java
import java.util.*;
public class NestedIterator implements Iterator<Integer> {
    private List<Integer> integers = new ArrayList<>();
    private int position = 0;

    public NestedIterator(List<NestedInteger> nestedList) {
        flattenList(nestedList);
    }

    private void flattenList(List<NestedInteger> nestedList) {
         for(NestedInteger ni: nestedList)
        {
            if(ni.isInteger())
            {
                integers.add(ni.getInteger());
            }
            else
            {
                flattenList(ni.getList());
            }
        }
        
    }

    @Override
    public Integer next() {
        return integers.get(position++);
        
    }
    @Override
    public boolean hasNext() {
        return position<integers.size();
        
    }
    public static List<NestedInteger> parse(String s) {
    Stack<List<NestedInteger>> stack = new Stack<>();
    List<NestedInteger> curr = new ArrayList<>();
    int num = 0;
    boolean hasNum = false;

    for (int i = 0; i < s.length(); i++) {
        char c = s.charAt(i);
        if (c == '[') {
            stack.push(curr);
            curr = new ArrayList<>();
        } else if (c == ']') {
            if (hasNum) {
                curr.add(new SimpleNestedInteger(num));
                hasNum = false;
                num = 0;
            }
            List<NestedInteger> completed = curr;
            curr = stack.pop();
            curr.add(new SimpleNestedInteger(completed));
        } else if (c == ',') {
            if (hasNum) {
                curr.add(new SimpleNestedInteger(num));
                hasNum = false;
                num = 0;
            }
        } else if (Character.isDigit(c)) {
            num = num * 10 + (c - '0');
            hasNum = true;
        }
    }
    return curr;
}


    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
      
        String input = sc.nextLine();

        List<NestedInteger> nestedList = parse(input);

        NestedIterator iterator = new NestedIterator(nestedList);
        List<Integer> output = new ArrayList<>();
        while (iterator.hasNext()) {
            output.add(iterator.next());
        }

        System.out.println(output);
    }
}

interface NestedInteger {
    boolean isInteger();
    Integer getInteger();
    List<NestedInteger> getList();
}

class SimpleNestedInteger implements NestedInteger {
    private Integer value;
    private List<NestedInteger> list;

    public SimpleNestedInteger(Integer value) {
        this.value = value;
        this.list = null;
    }

    public SimpleNestedInteger(List<NestedInteger> list) {
        this.list = list;
        this.value = null;
    }

    @Override
    public boolean isInteger() {
        return value != null;
    }

    @Override
    public Integer getInteger() {
        return value;
    }

    @Override
    public List<NestedInteger> getList() {
        return list;
    }
}

```
## Output:

![alt text](screenshots/image-5.png)

## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
