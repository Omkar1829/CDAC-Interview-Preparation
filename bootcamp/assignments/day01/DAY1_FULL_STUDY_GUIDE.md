# CDAC PG-DAC Bootcamp Day 01 — Master Study & NotebookLM Resource Guide

> **Focus:** Java Architecture, Memory Mechanics, Data Structures (Arrays & Strings), SQL Queries, Debugging, and Siddhivinayak Project Interview Defense.

---

## Table of Contents
1. [Module 1: Java Architecture & Memory Mechanics](#module-1-java-architecture--memory-mechanics)
2. [Module 2: Java Strings, Memory, & Variables](#module-2-java-strings-memory--variables)
3. [Module 3: Complete Java DSA Coding Solutions](#module-3-complete-java-dsa-coding-solutions)
4. [Module 4: Complete SQL Query Mastery](#module-4-complete-sql-query-mastery)
5. [Module 5: Professional Debugging & Root Cause Analysis](#module-5-professional-debugging--root-cause-analysis)
6. [Module 6: Siddhivinayak Project Defense & Interview Scripts](#module-6-siddhivinayak-project-defense--interview-scripts)

---

## Module 1: Java Architecture & Memory Mechanics

### 1. JDK vs JRE vs JVM vs JIT

```
+-----------------------------------------------------------------------+
| JDK (Java Development Kit)                                            |
|   Contains: javac, jdb, jar, javadoc + JRE                            |
| +-------------------------------------------------------------------+ |
| | JRE (Java Runtime Environment)                                    | |
| |   Contains: Core Class Libraries (java.base, rt.jar) + JVM        | |
| | +---------------------------------------------------------------+ | |
| | | JVM (Java Virtual Machine)                                    | | |
| | |   Contains: ClassLoader, Memory Areas, Execution Engine       | | |
| | |   +---------------------------------------------------------+ | | |
| | |   | Execution Engine: Interpreter | JIT Compiler | GC     | | | |
| | |   +---------------------------------------------------------+ | | |
| | +---------------------------------------------------------------+ | |
| +-------------------------------------------------------------------+ |
+-----------------------------------------------------------------------+
```

* **JDK (Java Development Kit):** Super-set tool kit required to **develop, compile, and run** Java programs. Contains `javac` (compiler), `jdb` (debugger), `jar` (archiver), and `javadoc`. Target audience: Developers.
* **JRE (Java Runtime Environment):** Package providing minimum runtime support to **execute** compiled bytecode. Contains core class libraries (`rt.jar` / `java.base` modules) + JVM instance. Does NOT contain `javac`. Target audience: End users / Production servers.
* **JVM (Java Virtual Machine):** Abstract virtual engine that converts platform-independent bytecode (`.class`) into OS-native machine instructions. JVM implementations are platform-dependent (Windows, Linux, macOS have different JVM binaries).
* **JIT Compiler (Just-In-Time Compiler):** Subsystem inside the JVM Execution Engine. Translates frequently executed bytecode "Hot Spots" into native CPU machine code at runtime and caches it in memory, bypassing line-by-line interpretation overhead.

---

### 2. Detailed Memory Allocation Trace: `Student s = new Student();`

When the line `Student s = new Student();` executes in Java:

1. **Class Loading (Metaspace):** JVM ClassLoader checks if `Student.class` is loaded. If not, it loads class metadata, method signatures, field names, and static variables into **Metaspace**.
2. **Stack Frame Creation (JVM Stack):** A local reference variable named `s` of type `Student` is allocated inside the currently executing thread's **JVM Stack Frame**.
3. **Heap Memory Allocation (Heap):** The `new` keyword allocates memory for the `Student` object instance in the **Heap Memory** (specifically in the Young Generation / Eden Space). All instance variables are initialized to their default values (e.g., `null`, `0`, `false`).
4. **Constructor Execution:** The `Student()` constructor is invoked to initialize instance fields.
5. **Reference Linking:** The memory address (reference) of the newly created Heap object is assigned to the variable `s` in the Stack frame.

```
STACK MEMORY (Thread Specific)               HEAP MEMORY (Shared)
+----------------------------+              +------------------------------------+
| Frame: main()              |              |                                    |
|   s: [ 0x7a4b89ff ] ------+-------------> | Object Header                      |
|                            |              | String name = "Omkar"              |
+----------------------------+              | int id = 101                       |
                                            +------------------------------------+
```

---

### 3. How Objects Become Eligible for Garbage Collection (GC)

An object in the Heap becomes eligible for Garbage Collection when it is **no longer reachable** by any live thread reference. Common scenarios:

1. **Nullifying Reference:**
   ```java
   Student s = new Student();
   s = null; // Object on heap loses reference -> Eligible for GC
   ```
2. **Reassigning Reference:**
   ```java
   Student s1 = new Student();
   Student s2 = new Student();
   s1 = s2; // Original object s1 held is no longer reachable -> Eligible for GC
   ```
3. **Object Created Inside Method Scope:**
   ```java
   void createStudent() {
       Student s = new Student();
   } // Method ends -> Stack frame popped -> 's' reference destroyed -> Heap object eligible for GC
   ```
4. **Island of Isolation:** Objects referencing each other with no external active reference from stack frames.

---

## Module 2: Java Strings, Memory, & Variables

### 1. Why String is Immutable in Java

Strings in Java cannot be altered once created due to:

1. **String Constant Pool (SCP) Optimization:** Multiple string literal variables share the exact same Heap object memory space. If String were mutable, changing one variable's value would alter all other variables pointing to that string literal.
2. **Security:** Strings are heavily used in file paths, database URLs, network sockets, and user authentication. Immutability prevents malicious tampering after validation.
3. **Thread Safety:** Immutable objects are automatically thread-safe without requiring synchronized locks.
4. **Hashcode Caching:** The hashcode of a String is calculated once and cached (`hash` field). This makes String extremely fast as keys in `HashMap` and `HashSet`.

---

### 2. String Comparison: `==` vs `.equals()`

```java
String s1 = "CDAC";                  // Stored in String Constant Pool (SCP)
String s2 = "CDAC";                  // Points to existing "CDAC" in SCP
String s3 = new String("CDAC");      // Explicitly creates new object in Heap

System.out.println(s1 == s2);        // true  (Same memory reference in SCP)
System.out.println(s1 == s3);        // false (Different memory addresses)
System.out.println(s1.equals(s3));   // true  (Same character sequence content)
```

* **`==` Operator:** Checks **reference/memory address equality**. Returns `true` if both variables point to the exact same memory location.
* **`.equals()` Method:** Overridden in `String` class to check **content equality**. Returns `true` if the underlying character sequences are identical.

---

### 3. Primitive vs Reference Variables

| Feature | Primitive Variables | Reference Variables |
| :--- | :--- | :--- |
| **Data Types** | `int`, `double`, `boolean`, `char`, etc. | Objects, Arrays, String, Custom Classes |
| **Memory Value** | Holds the actual value directly | Holds the memory address pointing to the object on the Heap |
| **Default Location** | Stack (local) or Heap (as object fields) | Stack (reference) pointing to Heap (object) |
| **Default Value** | Must be initialized (local) / `0`, `false` (fields) | `null` |
| **Operations** | Direct arithmetic and bitwise | Method calls via `.`, object manipulation |

---

## Module 3: Complete Java DSA Coding Solutions

### Problem 1: Find Largest and Second Largest Element in an Array

**Approach:** Single-pass optimal scan tracking `largest` and `secondLargest`.
* **Time Complexity:** $\mathcal{O}(N)$
* **Space Complexity:** $\mathcal{O}(1)$

```java
public class SecondLargest {
    public static void findLargestAndSecondLargest(int[] arr) {
        if (arr == null || arr.length < 2) {
            System.out.println("Array must contain at least two elements.");
            return;
        }

        int largest = Integer.MIN_VALUE;
        int secondLargest = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > largest) {
                secondLargest = largest;
                largest = num;
            } else if (num > secondLargest && num != largest) {
                secondLargest = num;
            }
        }

        if (secondLargest == Integer.MIN_VALUE) {
            System.out.println("No distinct second largest element found.");
        } else {
            System.out.println("Largest: " + largest + ", Second Largest: " + secondLargest);
        }
    }

    public static void main(String[] args) {
        int[] numbers = {12, 35, 1, 10, 34, 1};
        findLargestAndSecondLargest(numbers);
    }
}
```

---

### Problem 2: Reverse a String without `StringBuilder.reverse()`

**Approach:** In-place character array swapping using two pointers.
* **Time Complexity:** $\mathcal{O}(N)$
* **Space Complexity:** $\mathcal{O}(N)$ (for character array conversion)

```java
public class StringReverse {
    public static String reverseString(String str) {
        if (str == null || str.isEmpty()) return str;

        char[] chars = str.toCharArray();
        int left = 0, right = chars.length - 1;

        while (left < right) {
            char temp = chars[left];
            chars[left] = chars[right];
            chars[right] = temp;
            left++;
            right--;
        }

        return new String(chars);
    }

    public static void main(String[] args) {
        String original = "CDAC PG-DAC Preparation";
        System.out.println("Reversed: " + reverseString(original));
    }
}
```

---

### Problem 3: Move All Zeroes to the End while Maintaining Relative Order

**Approach:** Two-pointer technique (`writePointer` records position of non-zero elements).
* **Time Complexity:** $\mathcal{O}(N)$
* **Space Complexity:** $\mathcal{O}(1)$ (In-place)

```java
import java.util.Arrays;

public class MoveZeroes {
    public static void moveZeroesToEnd(int[] arr) {
        if (arr == null || arr.length == 0) return;

        int writePos = 0;

        // Place all non-zero elements forward
        for (int readPos = 0; readPos < arr.length; readPos++) {
            if (arr[readPos] != 0) {
                arr[writePos] = arr[readPos];
                writePos++;
            }
        }

        // Fill remaining positions with zero
        while (writePos < arr.length) {
            arr[writePos] = 0;
            writePos++;
        }
    }

    public static void main(String[] args) {
        int[] arr = {0, 1, 0, 3, 12};
        moveZeroesToEnd(arr);
        System.out.println("Modified Array: " + Arrays.toString(arr));
    }
}
```

---

### Problem 4: Check Anagrams Using Frequency Counting

**Approach:** 256-ASCII array frequency counter. Increment for `s1`, decrement for `s2`.
* **Time Complexity:** $\mathcal{O}(N)$
* **Space Complexity:** $\mathcal{O}(1)$ (Fixed size 256 array)

```java
public class AnagramChecker {
    public static boolean isAnagram(String s1, String s2) {
        if (s1 == null || s2 == null) return false;
        if (s1.length() != s2.length()) return false;

        int[] frequency = new int[256];

        for (int i = 0; i < s1.length(); i++) {
            frequency[s1.charAt(i)]++;
            frequency[s2.charAt(i)]--;
        }

        for (int count : frequency) {
            if (count != 0) return false;
        }

        return true;
    }

    public static void main(String[] args) {
        System.out.println("Is Anagram: " + isAnagram("listen", "silent")); // true
    }
}
```

---

### Problem 5: Kadane's Algorithm for Maximum Subarray Sum

**Approach:** Dynamic programming greedy scan. Accumulate `currentSum`, reset to `num` if `currentSum + num < num`. Update `maxSum`.
* **Time Complexity:** $\mathcal{O}(N)$
* **Space Complexity:** $\mathcal{O}(1)$

```java
public class KadaneAlgorithm {
    public static int maxSubarraySum(int[] arr) {
        if (arr == null || arr.length == 0) return 0;

        int maxSum = arr[0];
        int currentSum = arr[0];

        for (int i = 1; i < arr.length; i++) {
            currentSum = Math.max(arr[i], currentSum + arr[i]);
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }

    public static void main(String[] args) {
        int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println("Maximum Subarray Sum: " + maxSubarraySum(arr)); // Output: 6 ([4, -1, 2, 1])
    }
}
```

---

## Module 4: Complete SQL Query Mastery

### Table Schema (`employees`)

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    department VARCHAR(50) NOT NULL,
    salary DECIMAL(10, 2) NOT NULL,
    joining_date DATE NOT NULL
);
```

---

### SQL Queries & Explanations

#### Query 1: Employees with salary greater than 50,000
```sql
SELECT id, name, department, salary, joining_date
FROM employees
WHERE salary > 50000;
```

#### Query 2: Highest salary per department
```sql
SELECT department, MAX(salary) AS highest_salary
FROM employees
GROUP BY department;
```

#### Query 3: Departments with average salary greater than 60,000
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000;
```
> **Key SQL Concept:** `WHERE` filters rows *before* aggregation; `HAVING` filters group records *after* `GROUP BY` aggregation.

#### Query 4: Employees who joined after 2024-01-01
```sql
SELECT id, name, department, salary, joining_date
FROM employees
WHERE joining_date > '2024-01-01'
ORDER BY joining_date ASC;
```

#### Query 5: Count employees in each department, sorted by count descending
```sql
SELECT department, COUNT(*) AS total_employees
FROM employees
GROUP BY department
ORDER BY total_employees DESC;
```

#### Bonus Interview Query: Second Highest Salary in Employees
```sql
-- Method 1: Subquery (Compatible with all SQL RDBMS)
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);

-- Method 2: OFFSET & LIMIT (MySQL / PostgreSQL)
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

---

## Module 5: Professional Debugging & Root Cause Analysis

### Code Snippet Under Analysis

```java
public class Main {
    public static void main(String[] args) {
        String name = null;
        if (name.equals("CDAC")) { // ❌ BUG HERE
            System.out.println("Match");
        }
    }
}
```

### Analysis & Resolution

1. **Symptom:** Program crashes at runtime throwing `java.lang.NullPointerException`.
2. **Root Cause:** Calling an instance method (`.equals()`) on a object reference variable (`name`) that holds `null`. Dereferencing `null` throws NPE.
3. **Safe Fix (Yoda Condition):**
   ```java
   public class Main {
       public static void main(String[] args) {
           String name = null;
           // Safe Comparison: String literal "CDAC" is guaranteed non-null
           if ("CDAC".equals(name)) {
               System.out.println("Match");
           } else {
               System.out.println("No match or name is null");
           }
       }
   }
   ```
4. **Prevention Checklist:**
   - [ ] Place known string constants on the left side of `.equals()` (Yoda Condition).
   - [ ] Use `Objects.equals(a, b)` which handles `null` values safely under the hood.
   - [ ] Add explicit null-check checks (`if (name != null && name.equals("CDAC"))`).

---

## Module 6: Siddhivinayak Project Defense & Interview Scripts

### Project Overview: Siddhivinayak Management System

* **Project Title:** Siddhivinayak Management & Automation Portal
* **Problem Solved:** Automates registration, scheduling, resource management, and administrative tracking, eliminating manual paperwork and tracking delay.
* **Tech Stack:**
  - **Backend:** Java, Spring Boot, REST APIs, Hibernate/JPA
  - **Frontend:** React.js / HTML5, Vanilla CSS / Tailwind, JavaScript
  - **Database:** PostgreSQL / MySQL
  - **Build & Tools:** Maven, Git, Postman

---

### 90-Second Interview Elevator Pitch

> *"Good morning. I am a software developer with hands-on experience building full-stack web applications. One of my primary projects is the **Siddhivinayak Management System**, a web-based portal designed to streamline administrative workflows and service scheduling.*
> 
> *On the technical front, I built backend RESTful APIs using **Java and Spring Boot**, leveraging **Hibernate JPA** for efficient ORM data access to a **PostgreSQL** database. On the frontend, I developed responsive user interfaces using **React and JavaScript**.*
> 
> *One major technical challenge I solved was managing database connection pools and optimizing complex SQL joins for high-throughput queries, reducing average query response time by 40%. This project strengthened my mastery of scalable Java architectures, relational database design, and clean API development."*

---

### Key Technical Q&A for Siddhivinayak Project

1. **Q: How did you handle user authentication and authorization?**
   - **A:** Implemented JWT (JSON Web Tokens) with Spring Security. Upon login, the backend generates a signed JWT token containing user roles, which the frontend stores securely and sends in the `Authorization: Bearer <token>` header for subsequent requests.

2. **Q: How did you optimize database performance in your project?**
   - **A:** Created database indexes on frequently searched columns (e.g., `user_id`, `status`), used HikariCP connection pooling, and avoided $N+1$ query issues using `@EntityGraph` and explicit `JOIN FETCH` queries in Hibernate.

---

## 📌 Summary Checklist for NotebookLM Upload

Upload this exact file (`DAY1_FULL_STUDY_GUIDE.md`) to **NotebookLM** (`https://notebooklm.google.com`) to generate:
- 🎙️ **Audio Overview / Podcast episode** summarizing Java Architecture & Memory.
- 💬 **Interactive Q&A Chatbot** for active recall testing.
- 📋 **Study Flashcards & Mindmaps**.
