# Hibernate with PostgreSQL Setup Notes

## 1. Adding Dependencies

Add the following dependencies to your `pom.xml` file:

```xml
<dependencies>
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <version>42.7.3</version>
    </dependency>
    <dependency>
        <groupId>org.hibernate.orm</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>6.6.4.Final</version>
    </dependency>
</dependencies>
```

**Note:** Remember to refresh Maven after adding dependencies.

## 2. Configure Hibernate

Create a configuration file at `resources/hibernate.cfg.xml`:

```xml
<hibernate-configuration xmlns="http://www.hibernate.org/xsd/orm/cfg">
    <session-factory>
        <property name="hibernate.connection.driver_class">org.postgresql.Driver</property>
        <property name="hibernate.connection.url">jdbc:postgresql://localhost:5432/hibernate</property>
        <property name="hibernate.connection.username">postgres</property>
        <property name="hibernate.connection.password">katte2934</property>

        <property name="hibernate.hbm2ddl.auto">update</property>

        <property name="hibernate.dialect">org.hibernate.dialect.PostgreSQLDialect</property>
        
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>

    </session-factory>
</hibernate-configuration>
```

### Key Configuration Properties

- **hibernate.hbm2ddl.auto**: Controls schema generation
  - `update`: Updates the schema, preserving existing data
  - Other options: `create`, `create-drop`, `validate`, `none`

- **hibernate.dialect**: Specifies the SQL dialect to use
  - PostgreSQLDialect ensures Hibernate generates PostgreSQL-specific SQL

- **hibernate.show_sql**: Displays SQL queries in the console when set to true

- **hibernate.format_sql**: Makes the SQL output more readable when set to true

## 3. Entity Class

Create an entity class that maps to a database table:

```java
package com.vishwah;

import jakarta.persistence.Entity;
import jakarta.persistence.Id;

@Entity
public class Student {

    @Id
    private int rollNo;
    private String sName;
    private int sAge;
    
    // Getters and setters
    public int getRollNo() {
        return rollNo;
    }

    public void setRollNo(int rollNo) {
        this.rollNo = rollNo;
    }

    public String getsName() {
        return sName;
    }

    public void setsName(String sName) {
        this.sName = sName;
    }

    public int getsAge() {
        return sAge;
    }

    public void setsAge(int sAge) {
        this.sAge = sAge;
    }

    @Override
    public String toString() {
        return "Student{" +
                "rollNo=" + rollNo +
                ", sName='" + sName + '\'' +
                ", sAge=" + sAge +
                '}';
    }
}
```

### Annotations Explained

- **@Entity**: Marks the class as a JPA entity that will be mapped to a database table
- **@Id**: Indicates the primary key field of the entity

**Quick Hack**: You can generate getters, setters, and toString methods automatically in IntelliJ IDEA by right-clicking inside the class, selecting "Generate" and then choosing "Getter and Setter" or "toString()".

## 4. Main Application Code

```java
package com.vishwah;

import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;
import org.hibernate.cfg.Configuration;

public class Main {
    public static void main(String[] args) {

        // Create a Student object
        Student s1 = new Student();
        s1.setsAge(20);
        s1.setRollNo(257);
        s1.setsName("Hari");

        // Configuration and SessionFactory (refactored)
        SessionFactory sf = new Configuration()
                .addAnnotatedClass(com.vishwah.Student.class)
                .configure()
                .buildSessionFactory();

        // Open a session
        Session session = sf.openSession();

        // Begin transaction
        Transaction transaction = session.beginTransaction();

        // Persist data
        session.persist(s1);

        // Commit and close resources
        transaction.commit();
        session.close();
        sf.close();

        System.out.println(s1);
    }
}
```

### Key Components

- **Configuration**: Loads the hibernate configuration file and specifies annotated classes
  - Reads `hibernate.cfg.xml` and sets up connection parameters

- **SessionFactory**: Heavy-weight, thread-safe factory for Session objects
  - Expensive to create, typically created once during application initialization
  - Represents a connection pool to your database

- **Session**: Lightweight, single-threaded object representing a conversation with the database
  - Used to create, read, update, and delete persistent objects
  - Not thread-safe, should be opened when needed and closed when done

- **Transaction**: A unit of work with the database
  - Ensures ACID properties (Atomicity, Consistency, Isolation, Durability)
  - Must be committed to save changes or rolled back to undo changes

**Note on Refactoring**: `Configuration()` and `SessionFactory()` can be Defined in two seperate blocks if needed.