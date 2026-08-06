# Day 02 Study & Interview Preparation Guide

## 1. Today's Core Focus
OOP Architecture in Java, Linked List Data Structures, SQL Joins, and Day 01 High-Yield Revisions (Kadane's Algo + String Immutability).

---

## 2. Learning Objectives

- Explain the 4 Pillars of OOP with real-world & code examples.
- Distinguish between `Abstract Class` vs `Interface` (Java 8+ `default`/`static` methods).
- Master Method Overloading (Compile-time) vs Method Overriding (Runtime / Dynamic Method Dispatch).
- Master SQL Joins (`INNER`, `LEFT`, `RIGHT`, `FULL OUTER`, `SELF JOIN`).
- Solve Linked List problems (Reverse Linked List, Cycle Detection using Floyd's Tortoise & Hare algorithm).
- Revise Kadane's Algorithm ($O(N)$ array maximum subarray sum) carried over from Day 01.

---

## 3. High-Yield Theory Checklist

### A. Java Object-Oriented Programming (OOP)
1. **Abstraction vs Encapsulation:**
   - *Abstraction* hides complexity by showing only essential features (e.g., interfaces/abstract classes).
   - *Encapsulation* binds data (fields) and methods together and restricts direct access via access modifiers (`private` fields + `public` getters/setters).
2. **Method Overloading vs Method Overriding:**
   - *Overloading:* Same class, same method name, different parameter list (Compile-time polymorphism).
   - *Overriding:* Subclass redefines superclass method with same signature (Runtime polymorphism / Dynamic Method Dispatch).
3. **Abstract Class vs Interface (Java 8+):**
   - Abstract classes can have state (instance fields) and constructors.
   - Interfaces specify contract; since Java 8, can have `default` and `static` methods; Java 9 added `private` methods.
   - A class can extend only 1 abstract class but implement multiple interfaces.

### B. SQL Joins Matrix
- **`INNER JOIN`**: Returns matching rows in both tables.
- **`LEFT JOIN`**: Returns all rows from left table + matched rows from right table (`NULL` if no match).
- **`RIGHT JOIN`**: Returns all rows from right table + matched rows from left table (`NULL` if no match).
- **`FULL OUTER JOIN`**: Returns all rows when there is a match in left OR right table.
- **`SELF JOIN`**: Joining a table to itself (e.g., finding Employee-Manager relationships `WHERE emp.manager_id = mgr.id`).

---

## 4. Coding & DSA Tasks

### Task 1: Carryover - Kadane's Algorithm
- **Problem:** Find contiguous subarray with maximum sum in `int[] nums`.
- **Logic:** `currentSum = Math.max(nums[i], currentSum + nums[i])`, `maxSum = Math.max(maxSum, currentSum)`.
- **Target:** Write $O(N)$ code and state $O(1)$ space complexity without looking at notes.

### Task 2: Reverse a Singly Linked List
- **Problem:** Reverse a linked list in-place ($O(N)$ time, $O(1)$ space).
- **Pointers needed:** `prev = null`, `curr = head`, `next = null`.

### Task 3: Linked List Cycle Detection
- **Algorithm:** Floyd’s Cycle-Finding Algorithm (Slow and Fast Pointers).
- **Condition:** `slow = slow.next`, `fast = fast.next.next`. If `slow == fast`, cycle exists.

---

## 5. SQL Practice Query Tasks

Use two tables: `employees(id, name, dept_id, salary)` and `departments(dept_id, dept_name)`.

1. Write query to list all employee names along with their department names using `INNER JOIN`.
2. Write query to list all departments and the count of employees in each, including departments with 0 employees using `LEFT JOIN`.
3. Write query to find employees whose salary is higher than their manager's salary using `SELF JOIN` on `employees`.

---

## 6. Day 01 Carryover Revisions (Before Day 02 Mock)

- [ ] Explain **Why String is Immutable** (Security, Thread-Safety, SCP, HashCode Caching).
- [ ] Explain object creation for `String s = new String("CDAC");` (2 objects created if literal not in SCP).
- [ ] Explain Java Stack vs Heap allocation for `Student s = new Student();`.

---

## 7. Project Defense Polish (EduGuide-AI)

- Prepare 1-line bridge: *"Although EduGuide-AI backend was developed using ASP.NET Core & EF Core, the core RESTful architecture, relational schema design, PostgreSQL queries, and JWT auth flow map directly to Spring Boot and JPA/Hibernate."*
