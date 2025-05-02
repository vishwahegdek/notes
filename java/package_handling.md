# Java Packages - Quick Reference Guide

## 1. Define a Package
* Use `package` keyword at the top of your file
* Save the file in a directory structure matching the package name

```java
// File: mypackage/HelloWorld.java
package mypackage;

public class HelloWorld {
    public void sayHello() {
        System.out.println("Hello from the package!");
    }
}
```

## 2. Use the Package in Another File
* Use `import` to access classes from other packages

```java
// File: Main.java
import mypackage.HelloWorld;

public class Main {
    public static void main(String[] args) {
        HelloWorld hw = new HelloWorld();
        hw.sayHello();
    }
}
```

## 3. Project Structure
```
MyProject/
├── Main.java
└── mypackage/
    └── HelloWorld.java
```

## 4. Compile and Run
From inside `MyProject/` folder:

```bash
javac mypackage/HelloWorld.java
javac Main.java
java Main
```

Output:
```
Hello from the package!
```

## 5. Additional Package Tips

### Package Naming Convention
* Use reverse domain naming: `com.company.project.module`
* Use lowercase letters for package names
* Example: `com.example.util.math`

### Import Variations
```java
// Import a specific class
import mypackage.HelloWorld;

// Import all classes in a package (use with caution)
import mypackage.*;
```

### Fully Qualified Names
You can use classes without importing by using fully qualified names:

```java
public class Main {
    public static void main(String[] args) {
        mypackage.HelloWorld hw = new mypackage.HelloWorld();
        hw.sayHello();
    }
}
```

### Creating Multi-Level Packages
```java
// File: com/example/util/StringUtils.java
package com.example.util;

public class StringUtils {
    // methods here
}
```

With corresponding directory structure:
```
MyProject/
├── Main.java
└── com/
    └── example/
        └── util/
            └── StringUtils.java
```