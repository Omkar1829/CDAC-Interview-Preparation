# Day 03 High-Yield Interview Questions

## Q1: How does HashMap work internally in Java 8+?
**Answer**:
- `HashMap` stores data as key-value pairs in an array of bucket nodes (`Node<K,V>[] table`).
- Key's hash index is calculated via `hash(key) & (table.length - 1)`.
- When multiple keys map to the same bucket index (Collision), Java handles it via LinkedList chaining.
- In **Java 8+**, if bucket size exceeds 8 (`TREEIFY_THRESHOLD`) and array capacity $\ge 64$, the LinkedList is converted into a Red-Black Tree to improve worst-case search time from $O(N)$ to $O(\log N)$.

## Q2: What happens if two objects return the same `hashCode()`?
**Answer**:
They are placed in the same bucket in the `HashMap`. This is called a **Hash Collision**. The `HashMap` then calls `.equals()` on the keys in that bucket sequentially to find or insert the exact key.

## Q3: What is the difference between `EXISTS` and `IN` in SQL?
**Answer**:
- `EXISTS` checks for row existence and returns `TRUE` as soon as a single matching row is found (short-circuiting). It handles `NULL` values safely.
- `IN` fetches all values from the subquery and checks if the outer value exists in the returned list. If the subquery result contains a `NULL`, `NOT IN` returns empty results unexpectedly.

## Q4: Explain the Spring Boot request execution flow.
**Answer**:
HTTP Request ➔ `DispatcherServlet` (Front Controller) ➔ `@RestController` (Handles HTTP mapping & input validation) ➔ `@Service` (Executes business logic & manages transactions) ➔ `@Repository` (Spring Data JPA executes SQL queries) ➔ Database.
