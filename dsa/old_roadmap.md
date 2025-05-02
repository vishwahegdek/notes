# Java Data Structures and Algorithms (DSA) Guide

## 1. Project Structure for DSA Practice

Keep your project structure simple but organized for learning:

```
dsa-java/
└── src/
    ├── arrays/
    │    └── ArrayBasics.java
    ├── linkedlists/
    │    └── SinglyLinkedList.java
    ├── stacks/
    │    └── StackUsingArray.java
    ├── queues/
    │    └── QueueUsingLinkedList.java
    └── trees/
         └── BinaryTree.java
```

Key idea: Each DSA topic has its own folder/package and separate Java files for each major concept.

### Example Package and File

**src/arrays/ArrayBasics.java**:
```java
package arrays;

public class ArrayBasics {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        printArray(arr);
    }

    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

## 2. How to Segregate Classes and Methods

### For Algorithms (like Binary Search)

**src/arrays/BinarySearch.java**:
```java
package arrays;

public class BinarySearch {
    public static int binarySearch(int[] arr, int target) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] == target) {
                return mid;
            } else if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9};
        int target = 7;
        int index = binarySearch(arr, target);
        System.out.println("Index of " + target + " is: " + index);
    }
}
```

### For Data Structures (like Linked List)

**src/linkedlists/SinglyLinkedList.java**:
```java
package linkedlists;

public class SinglyLinkedList {
    Node head;

    static class Node {
        int data;
        Node next;

        Node(int d) {
            data = d;
            next = null;
        }
    }

    public void printList() {
        Node n = head;
        while (n != null) {
            System.out.print(n.data + " ");
            n = n.next;
        }
    }

    public static void main(String[] args) {
        SinglyLinkedList list = new SinglyLinkedList();
        list.head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);

        list.head.next = second;
        second.next = third;

        list.printList();
    }
}
```

## 3. Java Coding Conventions

| Element | Convention |
|---------|------------|
| File name | Must match the public class name |
| Package names | All lowercase (e.g., `arrays`, `linkedlists`) |
| Class names | PascalCase (e.g., `SinglyLinkedList`, `BinarySearch`) |
| Method names | camelCase (e.g., `printArray()`, `binarySearch()`) |
| Constants | ALL_CAPS (e.g., `static final int MAX_SIZE = 100;`) |
| Indentation | 4 spaces per level |
| Braces `{}` | Same line as statement: `public void foo() { ... }` |
| Comments | `//` for single-line, `/* */` for block comments |

### Example of Good Style

```java
public class Example {
    public static void main(String[] args) {
        System.out.println("Good style matters!");
    }
}
```

## 4. Compiling & Running Your Code

From the `src` folder:

```bash
# Compile a single file
javac arrays/ArrayBasics.java

# Run the compiled class
java arrays.ArrayBasics

# Compile multiple files
javac arrays/*.java linkedlists/*.java
```

## 5. DSA Learning Path

1. **Arrays & Strings**
   - Basic array operations
   - Linear search & Binary search
   - Array rotations
   - String manipulation

2. **Linked Lists**
   - Singly & Doubly linked lists
   - Insertion, deletion, traversal
   - Finding middle element
   - Detecting cycles

3. **Stacks & Queues**
   - Implementation using arrays and linked lists
   - Applications (balancing parentheses, etc.)

4. **Trees**
   - Binary trees & Binary search trees
   - Tree traversals (inorder, preorder, postorder)
   - Height & depth calculations

5. **Graphs**
   - Representation (adjacency matrix, adjacency list)
   - DFS & BFS traversals
   - Path finding algorithms

6. **Sorting Algorithms**
   - Bubble sort, Selection sort, Insertion sort
   - Merge sort, Quick sort
   - Understanding time and space complexity

7. **Searching Algorithms**
   - Linear search, Binary search
   - Hashing

8. **Advanced Data Structures**
   - Heaps
   - HashMaps
   - Tries
   - Segment Trees

## 6. Best Practices for Java DSA Implementation

1. **Focus on readability** - Clear variable names, comments for complex logic
2. **Test each component** - Write test cases for edge conditions
3. **Analyze time & space complexity** - Get in the habit of calculating Big O
4. **Implement incrementally** - Build basic functionality before optimizing
5. **Document your code** - Use Javadoc style comments for methods
6. **Review standard implementations** - Study Java's own collections framework

## 7. Resources for Learning Java DSA

- **Books**:
  - "Data Structures and Algorithms in Java" by Robert Lafore
  - "Introduction to Algorithms" by Cormen, Leiserson, Rivest, and Stein
  - "Algorithms" by Robert Sedgewick and Kevin Wayne

- **Online Platforms**:
  - LeetCode
  - HackerRank
  - GeeksforGeeks

- **Java-Specific Resources**:
  - Java Documentation
  - Oracle Java Tutorials