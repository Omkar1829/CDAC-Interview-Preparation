# Mock Interview 01 — Questions & Responses Log

> **Date:** August 04, 2026  
> **Session:** Day 01 Evaluation & Review  
> **Overall Score:** 7.5 / 10 (Status: Re-evaluate Day 02 for String Pool & DSA)

---

## 1. Java Core & Memory Mechanics

### Q1: Explain JVM, JRE, and JDK with their key differences.
* **Candidate Response:**
  > *"JDK (Java Development Kit) is the complete toolkit for developers containing `javac`, `jdb`, `jar`, and `javadoc` along with the JRE. JRE (Java Runtime Environment) provides the execution environment with core class libraries (`rt.jar` / `java.base`) and the JVM. JVM (Java Virtual Machine) is the platform-dependent virtual engine that executes bytecode line-by-line using Interpreter and JIT Compiler."*
* **Score:** 10 / 10
* **Feedback:** Excellent clarity and structural precision.

---

### Q2: Walk me through the exact memory allocation for `Student s = new Student();`.
* **Candidate Response:**
  > *"First, `Student.class` bytecode is loaded into Metaspace. Next, reference variable `s` is allocated on the thread's JVM Stack frame. The `new` keyword allocates memory for the `Student` object instance in Heap memory. Finally, the constructor initializes instance fields and the Heap address is stored in `s`."*
* **Score:** 10 / 10
* **Feedback:** Flawless step-by-step trace covering Metaspace, Stack, and Heap memory areas.

---

### Q3: Why is String immutable in Java, and how many objects are created by `new String("CDAC")`?
* **Candidate Response:**
  > *"String is immutable for String Constant Pool optimization, security, and thread safety. `new String("CDAC")` creates 1 object on the Heap."*
* **Score:** 7 / 10
* **Feedback (Area for Improvement):** Missed explaining the String Constant Pool (SCP) check. Correct answer: It creates **2 objects** if `"CDAC"` is not already in the SCP (1 object in Heap, 1 literal in SCP). If `"CDAC"` already exists in SCP, it creates **1 object** on Heap.

---

## 2. SQL Query Mastery

### Q1: Write a query to find employees with salary > 50,000.
* **Candidate Response:**
  ```sql
  SELECT id, name, department, salary, joining_date
  FROM employees
  WHERE salary > 50000;
  ```
* **Score:** 10 / 10

---

### Q2: Write a query for highest salary per department, and departments with average salary > 60,000. Explain `WHERE` vs `HAVING`.
* **Candidate Response:**
  ```sql
  -- Highest salary per department
  SELECT department, MAX(salary) AS highest_salary
  FROM employees
  GROUP BY department;

  -- Avg salary > 60,000
  SELECT department, AVG(salary) AS avg_salary
  FROM employees
  GROUP BY department
  HAVING AVG(salary) > 60000;
  ```
  > *"`WHERE` filters individual rows before `GROUP BY` aggregation, while `HAVING` filters aggregated group summary rows after `GROUP BY`."*
* **Score:** 10 / 10
* **Feedback:** Perfect SQL syntax and accurate explanation of execution order.

---

## 3. Debugging & Code Analysis

### Q1: Identify and fix the bug in `if (name.equals("CDAC"))` when `name = null`.
* **Candidate Response:**
  > *"It throws a `NullPointerException` because `.equals()` is called on a `null` variable reference `name`. The safe fix is Yoda condition: `"CDAC".equals(name)` or using `Objects.equals(name, "CDAC")`."*
* **Score:** 9 / 10
* **Feedback:** Solid diagnosis and clean production-ready solution.

---

## 4. Project Interview Defense (Siddhivinayak / EduGuide-AI)

### Q1: Give your 90-second technical elevator pitch.
* **Candidate Response:**
  > *"I developed a full-stack web application with RESTful APIs in Spring Boot / ASP.NET Core, ORM database access via JPA / EF Core to PostgreSQL, and responsive React UIs. I optimized HikariCP connection pooling and SQL queries, reducing API latency by 40%."*
* **Score:** 9.5 / 10
* **Feedback:** Strong technical presentation highlighting metrics and architecture.

---

## 5. Summary & Day 02 Action Plan

| Category | Score | Result | Next Step |
|---|---|---|---|
| Java Core | 9.0 / 10 | Passed | Revise String Constant Pool count rules |
| SQL | 10 / 10 | Passed | Proceed to SQL Joins |
| Debugging | 9.0 / 10 | Passed | Maintain Yoda condition practice |
| Project Defense | 9.5 / 10 | Passed | Link backend architecture to Java JPA |
| DSA | Pending | Pending | Complete Kadane's Algorithm $O(N)$ proof on Day 02 |
