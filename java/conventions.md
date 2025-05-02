# Java Conventions & DSA Project Structure

## ✅ Java Naming Conventions

| Element | Convention | Example |
|---------|------------|---------|
| File name | Must match the public class name | `SinglyLinkedList.java` |
| Package names | All lowercase | `arrays`, `linkedlists` |
| Class names | PascalCase | `SinglyLinkedList`, `BinarySearch` |
| Method names | camelCase | `printArray()`, `binarySearch()` |
| Constants | ALL_CAPS | `static final int MAX_SIZE = 100;` |
| Indentation | 4 spaces per level | |
| Braces `{}` | Same line as statement | `public void foo() { ... }` |
| Comments | `//` for single-line, `/* */` for blocks | |



## 📂 Project Structure for DSA Practice

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

- Organize each DSA topic in its own folder/package (arrays, stacks, etc.)
- Each major concept should have its own Java file




## 🛠️ Class and Method Organization

### Example: Basic Array Operations

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

### Example: Binary Search Algorithm

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

### Example: Linked List Implementation

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



## 🔍 Compiling & Running Java Code

From the `src` folder:

```bash
# Compile a single file
javac arrays/ArrayBasics.java

# Run a class
java arrays.ArrayBasics

# Compile multiple files
javac arrays/*.java linkedlists/*.java
```

## 🚀 Learning Path

1. Create the project structure with folders for each DSA topic
2. Start with arrays: implement searching, sorting algorithms
3. Move to linked lists, stacks, queues, then trees
4. Follow good coding conventions consistently
5. Practice compiling/running from the terminal