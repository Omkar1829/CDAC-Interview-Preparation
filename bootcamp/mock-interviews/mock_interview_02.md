# Mock Interview 02 — Questions & Responses Log

> **Date:** August 05, 2026  
> **Session:** Day 02 Mock Technical Interview (OOP Concepts, Linked Lists & SQL Joins)  
> **Status:** In Progress (Q1 Submitted)

---

## 1. Java & OOP Concepts

### Q1: Explain the difference between Abstraction and Encapsulation with a real-world software example.
* **Candidate Response:**
  > *"Encapsulation is used to protect direct data access and wrapping methods and fields in one data set; the example of encapsulation is a class. Abstraction is hiding the implementation and showing only essential methods to work with. In real life, a LAPTOP provides several functions like displaying information, keyboard input, USB ports—all bundled into one laptop (Encapsulation). Abstraction is the keyboard: when we press a key it displays that character, but internally how semiconductor transmitters work is hidden and we don't care about it."*
* **Score:** 9.5 / 10
* **Evaluator Feedback:** Outstanding definitions and real-world analogies (Laptop casing for Encapsulation, Keyboard key-press for Abstraction).
* **Interviewer Cross-Question:** In Java, if a field is `private` but has `public` getters/setters without validation, is Encapsulation broken or still valid?
* **Candidate Defense:**
  > *"Getter/setters are methods, and to maintain encapsulation we write methods to access data so it is still valid Encapsulation."*
* **Evaluator Feedback:** **10 / 10** — Correct! It is still valid Encapsulation because data fields are protected behind controlled access methods (`private` modifier + `public` API). The class retains control over access and internal representations can be modified or validated later without breaking caller code.

---

### Q2: What is the difference between Method Overloading and Method Overriding? Can we override a `static` method in Java? Why or why not?
* **Candidate Response:**
  > *"Method Overloading is compile-time polymorphism where there is same name with different parameters (or types). Method Overriding is runtime polymorphism where the method name is the same but implementation is different. Static methods belong to the class, not to object instances, which is why we cannot override static methods in Java."*
* **Score:** 9.0 / 10
* **Evaluator Feedback:** Excellent identification of compile-time vs runtime polymorphism and class-level static binding! Note: In Overriding, the method signature must be *identical*; in Overloading, parameter types/counts differ.
* **Interviewer Cross-Question:** What is it called when a subclass defines a static method with the same signature as a superclass static method, and which method executes for `Parent p = new Child(); p.staticMethod()`?
* **Candidate Defense:**
  > *"If we refer to the Parent class reference and call the static method, it calls the Parent class static method."*
* **Evaluator Feedback:** **9.0 / 10** — Correct execution deduction! The phenomenon is called **Method Hiding**. Because static methods are bound at compile time based on reference type (`Parent`), `p.staticMethod()` executes `Parent.staticMethod()` regardless of the runtime object (`Child`).

---

### Q3: Can an Abstract Class have a constructor in Java? What are `default` and `static` methods introduced in Java 8 Interfaces?
* **Candidate Response:**
  > *"Yes, abstract class has a constructor, but it initializes when we call/instantiate the child class. Every field of interface is public static final."*
* **Score:** 7.5 / 10
* **Evaluator Feedback:** Excellent answer on Abstract Class constructors (invoked via `super()` during subclass instantiation). Note on Interfaces:
  - Interface **Variables/Fields** are `public static final` (constants).
  - Interface **Methods (Pre-Java 8)** were `public abstract`.
  - **Java 8 `default` methods:** Concrete methods with a body inside an interface introduced for **backward compatibility** (adding new methods without breaking existing implementing classes).
  - **Java 8 `static` methods:** Utility methods called via `InterfaceName.methodName()`.
* **Interviewer Cross-Question Pending:** What problem occurs if a class implements two interfaces that both have a `default` method with the exact same signature (Diamond Problem)?

---

### Q4: How many total objects are created for `String s1 = "CDAC"; String s2 = new String("CDAC");`?
* **Candidate Response:**
  > *"1 object only and CDAC is getting stored in string pool and s2 refers the same string pool."*
* **Score:** 6.5 / 10
* **Evaluator Feedback & High-Yield Concept:**
  - Total objects created = **2 objects**!
  - **Line 1 (`String s1 = "CDAC";`):** Creates **1 object** in the String Constant Pool (SCP). `s1` points directly to SCP.
  - **Line 2 (`String s2 = new String("CDAC");`):** The `new` keyword **ALWAYS allocates a new object in Heap memory**. It takes `"CDAC"` from SCP and creates a separate object in Heap. `s2` points to the **Heap object**, NOT directly to SCP.
---

## 2. Data Structures & Algorithms (LeetCode Submissions)

### Q5: LeetCode #7 — Reverse Integer (Medium) & LeetCode #9 — Palindrome Number (Easy)
* **Candidate Submissions & Verification:**
  - **LeetCode #7 (Reverse Integer - Solved):**
    ```java
    class Solution {
        public int reverse(int x) {
            int reverse = 0;
            while (x != 0) {
                int digit = x % 10;
                if (reverse > Integer.MAX_VALUE / 10 || (reverse == Integer.MAX_VALUE / 10 && digit > 7)) return 0;
                if (reverse < Integer.MIN_VALUE / 10 || (reverse == Integer.MIN_VALUE / 10 && digit < -8)) return 0;
                reverse = reverse * 10 + digit;
                x = x / 10;
            }
            return reverse;
        }
    }
    ```
  - **LeetCode #9 (Palindrome Number - Solved):**
    ```java
    class Solution {
        public boolean isPalindrome(int x) {
            if (x < 0) return false;
            int revNum = 0, num = x;
            while (num != 0) {
                int digit = num % 10;
                revNum = (revNum * 10) + digit;
                num = num / 10;
            }
            return revNum == x;
        }
    }
    ```
* **Score:** **10 / 10**
---

## 3. SQL & Relational Joins

### Q6: Explain the difference between `INNER JOIN` and `LEFT JOIN`. How do NULL values behave in both?
* **Candidate Response:**
  > *"In INNER JOIN we only get common matching values of both tables. In LEFT JOIN we get all values of the left table plus matching values of the right table. If a left table record has no match in the right table, right table columns display NULL."*
* **Score:** **9.0 / 10**
---

### Q7: What is a `SELF JOIN`? Write a query to find employees earning more than their manager.
* **Candidate Response:**
  ```sql
  SELECT
      e.ename AS employee,
      e.sal AS employee_sal,
      m.ename AS manager,
      m.sal AS manager_sal
  FROM emp e
  JOIN emp m
  ON e.mgr = m.empno
  WHERE e.sal > m.sal;
  ```
* **Score:** **10 / 10**
---

## 4. Project & HR Evaluation

### Q8: Project Architectural Bridge
* **Candidate Response:**
  > *"For ASP.NET Core I will use Spring Boot, for EF Core I will use Hibernate and PostgreSQL, and React as usual for frontend because React has rich library support and builds scalable UI."*
* **Score:** **9.0 / 10**
* **Evaluator Feedback:** Excellent technology mapping (ASP.NET Core $\rightarrow$ Spring Boot, EF Core $\rightarrow$ Hibernate/JPA, PostgreSQL DB, React SPA frontend).

---

### Q9: Technical HR Question — Why should we hire you?
* **Candidate Response:**
  > *"I am a fast learner. ASP.NET and J2EE share nearly identical enterprise architecture patterns (MVC, ORM, REST) so I can adapt in no time because the core OOP fundamentals are identical."*
* **Score:** **9.5 / 10**
* **Evaluator Feedback:** Outstanding answer! Highlighted core OOP principles, rapid framework adaptability, and strong technical confidence.

---

## 📊 Final Mock Interview 02 Summary

* **Overall Score:** **9.0 / 10**
* **Result:** **PASSED 🟩 (Mastered Day 02)**
* **Category Scores:**
  - OOP Concepts & Java Theory: `8.8 / 10`
  - DSA & Math (LeetCode 7 & 9): `10 / 10`
  - SQL Joins & Queries: `9.5 / 10`
  - Project Bridge & HR Pitch: `9.25 / 10`


* **Interviewer Cross-Question Pending:** How do we write a `LEFT JOIN` query with `WHERE right_table.id IS NULL` to find records in Table A that do NOT exist in Table B (Anti-Join Pattern)?







