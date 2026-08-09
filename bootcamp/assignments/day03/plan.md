# Day 03 Detailed Schedule & Execution Plan

## Morning Session (09:00 - 12:30) - Core Java Theory & Collections

1. **Java Collections Hierarchy (09:00 - 10:30)**
   - `Collection` interface: `List` (`ArrayList`, `LinkedList`, `Vector`), `Set` (`HashSet`, `LinkedHashSet`, `TreeSet`), `Queue` (`PriorityQueue`, `ArrayDeque`).
   - `Map` interface hierarchy: `HashMap`, `LinkedHashMap`, `TreeMap`, `Hashtable`, `ConcurrentHashMap`.

2. **HashMap Deep-Dive (10:30 - 12:30)**
   - Default initial capacity (16), load factor (0.75), threshold calculation.
   - Buckets & Hash index calculation: `index = hash(key) & (n - 1)`.
   - Collision handling: Chaining (LinkedList) to Red-Black Tree (Treeification when bucket length $\ge 8$ and table capacity $\ge 64$).
   - `hashCode()` and `equals()` contract & custom keys implementation.
   - Interface default vs static methods (Day 02 carryover review).

---

## Afternoon Session (13:30 - 17:00) - Data Structures & Algorithms

1. **Stack & Queue Fundamentals (13:30 - 14:30)**
   - LIFO (Stack) vs FIFO (Queue).
   - Array & LinkedList based implementations.

2. **Coding Problems (14:30 - 17:00)**
   - **Problem 1**: Valid Parentheses (LeetCode 20) - Stack matching.
   - **Problem 2**: Implement Queue using Stacks (LeetCode 232) - Two stacks push/pop amortized $O(1)$.
   - **Problem 3**: Next Greater Element I (LeetCode 496) - Monotonic Stack technique.

---

## Evening Session (17:30 - 20:00) - SQL & Spring Boot Prep

1. **SQL Subqueries & Aggregations (17:30 - 19:00)**
   - Scalar vs Column vs Table subqueries.
   - Correlated Subqueries vs Non-correlated Subqueries.
   - Performance & behavior: `EXISTS` vs `IN` (handling `NULL` values).
   - Practical Query: 2nd Highest Salary per Department using subquery and `DENSE_RANK()`.

2. **Spring Boot Architectural Flow (19:00 - 20:00)**
   - Client HTTP Request ➔ `DispatcherServlet` ➔ `Controller` (`@RestController`) ➔ `Service` (`@Service`) ➔ `Repository` (`@Repository` / Spring Data JPA) ➔ DB Entity.
