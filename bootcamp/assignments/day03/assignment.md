# Day 03 Study & Interview Preparation Guide

## 1. Today's Core Focus
Java Collections Framework, HashMap Internals, Stack & Queue Data Structures, SQL Subqueries (`EXISTS` vs `IN`), and Spring Boot Architectural Flow.

---

## 2. Learning Objectives

- Explain `List` vs `Set` vs `Map` and internal data structures behind `ArrayList`, `HashSet`, `TreeSet`, and `HashMap`.
- Master `HashMap` internal mechanics: Hash function, bucket indexing, collision resolution via chaining, and Java 8 Red-Black Tree treeification.
- Articulate the strict `hashCode()` and `equals()` contract in Java.
- Solve fundamental Stack & Queue DSA problems: Valid Parentheses, Implement Queue using Stacks, and Next Greater Element.
- Master SQL Subqueries: Correlated subqueries, `EXISTS` vs `IN` performance, and Nth highest salary logic.
- Explain the end-to-end Spring Boot application flow (`Controller` ➔ `Service` ➔ `Repository`).

---

## 3. High-Yield Theory Checklist

### A. Java Collections Framework & HashMap Internals
1. **List vs Set vs Map:**
   - `List`: Ordered collection, allows duplicate elements (`ArrayList`, `LinkedList`, `Vector`).
   - `Set`: Unordered collection, unique elements only (`HashSet` backed by `HashMap`, `TreeSet` backed by `TreeMap`).
   - `Map`: Key-Value pairs, unique keys (`HashMap`, `LinkedHashMap`, `TreeMap`, `ConcurrentHashMap`).
2. **HashMap Internal Working (Java 8+):**
   - Default Capacity: 16 | Default Load Factor: 0.75 | Threshold: $16 \times 0.75 = 12$.
   - Index Calculation: `hash = key.hashCode() ^ (hash >>> 16)`, `index = hash & (n - 1)`.
   - Treeification: When a bucket's node count exceeds `TREEIFY_THRESHOLD` (8) and array capacity $\ge 64$, the LinkedList turns into a Red-Black Tree ($O(N) \to O(\log N)$ search).
3. **`hashCode()` & `equals()` Contract:**
   - If `a.equals(b)` is `true`, then `a.hashCode() == b.hashCode()` MUST be `true`.
   - If `a.hashCode() == b.hashCode()`, `a.equals(b)` may be `true` or `false` (Collision).
   - If overriding `equals()`, always override `hashCode()`; otherwise `HashMap` lookup fails.

### B. SQL Subqueries & Aggregations
- **Correlated Subquery:** Inner query depends on current row evaluated by outer query (e.g., `WHERE salary > (SELECT AVG(salary) FROM emp e2 WHERE e2.dept_id = e1.dept_id)`).
- **`EXISTS` vs `IN`:**
  - `EXISTS` returns boolean as soon as a match is found (short-circuiting); handles `NULL` safely.
  - `IN` compares values against a list/subquery result; fails unexpectedly when subquery returns `NULL`.
  - `EXISTS` is usually faster for large outer/inner datasets when filtered by subqueries.

---

## 4. Coding & DSA Tasks

### Task 1: Valid Parentheses (LeetCode 20)
- **Problem:** Given string `s` containing `'('`, `')'`, `'{'`, `'}'`, `'['`, `']'`, determine if valid.
- **Logic:** Use a Stack of characters. Push opening brackets, pop & match for closing brackets.

### Task 2: Implement Queue using Stacks (LeetCode 232)
- **Problem:** Implement FIFO Queue using two LIFO Stacks (`stackIn` and `stackOut`).
- **Amortized Complexity:** Push $O(1)$, Pop/Peek amortized $O(1)$.

### Task 3: Next Greater Element I (LeetCode 496)
- **Problem:** Find next greater element for each array element.
- **Algorithm:** Use a Monotonic Decreasing Stack and HashMap to store mappings in $O(N)$ time.

---

## 5. SQL Practice Query Tasks

Use tables `employees(emp_id, emp_name, dept_id, salary)` and `departments(dept_id, dept_name)`.

1. Write a query to find employees earning more than the average salary of their respective department using a **Correlated Subquery**.
2. Write a query to list departments that have at least one employee using `EXISTS`.
3. Write a query to find the **2nd Highest Salary per Department** using `DENSE_RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC)`.

---

## 6. Spring Boot Architecture Flow

- **Client Request** ➔ HTTP GET/POST to `/api/v1/employees`.
- **`DispatcherServlet`**: Front Controller routes request to appropriate Handler Mapping.
- **`Controller` (`@RestController`)**: Handles request mapping, payload validation (`@Valid`), returns DTO/ResponseEntity.
- **`Service` (`@Service`)**: Contains core business logic, transaction management (`@Transactional`).
- **`Repository` (`@Repository`)**: Interacts with Database via Spring Data JPA / Hibernate / JDBC.
