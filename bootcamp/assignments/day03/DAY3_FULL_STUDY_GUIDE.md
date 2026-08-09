# Day 03 Comprehensive Study Guide

## 1. Java Collections Framework Deep Dive

### 1.1 Collections Hierarchy Overview
```
                   Iterable<E>
                        │
                   Collection<E>
       ┌────────────────┼────────────────┐
    List<E>          Set<E>           Queue<E>
    ├── ArrayList    ├── HashSet      ├── PriorityQueue
    ├── LinkedList   ├── LinkedHashSet└── ArrayDeque
    └── Vector       └── TreeSet

                    Map<K,V> (Separate Hierarchy)
       ┌────────────────┼────────────────┐
   HashMap<K,V>   LinkedHashMap<K,V> TreeMap<K,V>
```

### 1.2 HashMap Internal Mechanics
1. **Node Structure (`Node<K,V>`)**:
   ```java
   static class Node<K,V> implements Map.Entry<K,V> {
       final int hash;
       final K key;
       V value;
       Node<K,V> next;
   }
   ```
2. **Hash Code & Index Formula**:
   - `hash = (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16)`
   - `index = (n - 1) & hash` (where $n$ is table capacity, power of 2).
3. **Collision & Treeification**:
   - Initial capacity: 16.
   - When bucket collision happens, nodes form a linked list.
   - **Treeification Threshold**: If a single bucket length $> 8$ and total array size $\ge 64$, LinkedList converts to a **Red-Black Tree** (`TreeNode<K,V>`).
   - Search time reduces from $O(N)$ (list) to $O(\log N)$ (tree).
   - **Untreeification Threshold**: If elements in a tree bucket reduce to $\le 6$, it converts back to a LinkedList.

### 1.3 `hashCode()` & `equals()` Rules
- If `obj1.equals(obj2)` is `true`, `obj1.hashCode() == obj2.hashCode()` MUST be `true`.
- If `obj1.hashCode() == obj2.hashCode()`, `obj1.equals(obj2)` CAN be `true` or `false`.
- **Why custom keys need both overridden**:
  - `HashMap` first compares hash codes to find the bucket index.
  - Then uses `equals()` to find the exact key in the bucket.
  - Failing to override `hashCode()` causes keys to map to different buckets, making `map.get(key)` return `null` even if key values match.

---

## 2. Stacks & Queues

### Stack (LIFO)
- Operations: `push()`, `pop()`, `peek()`, `isEmpty()`.
- Use Cases: Function call stack, Undo/Redo, Expression parsing, Monotonic stack problems.

### Queue (FIFO)
- Operations: `offer()`, `poll()`, `peek()`.
- Implementation: `LinkedList` or `ArrayDeque`.
- Implementation using 2 Stacks (`inStack`, `outStack`):
  - Push: `inStack.push(x)` -> $O(1)$.
  - Pop: If `outStack` is empty, pop all elements from `inStack` and push into `outStack`. Then `outStack.pop()` -> Amortized $O(1)$.

---

## 3. SQL Subqueries (`EXISTS` vs `IN`)

### Correlated Subquery Example
```sql
SELECT e1.emp_name, e1.salary, e1.dept_id
FROM employees e1
WHERE e1.salary > (
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.dept_id = e1.dept_id
);
```

### `EXISTS` vs `IN`
```sql
-- Using EXISTS (Short-circuits upon first match)
SELECT d.dept_name
FROM departments d
WHERE EXISTS (
    SELECT 1 FROM employees e WHERE e.dept_id = d.dept_id
);

-- Using IN
SELECT d.dept_name
FROM departments d
WHERE d.dept_id IN (
    SELECT e.dept_id FROM employees e
);
```

---

## 4. Spring Boot Architectural Flow

```
[Client / UI]
     │ (HTTP Request: GET /api/v1/users)
     ▼
[DispatcherServlet]
     │ (Route to controller)
     ▼
[@RestController UserControler]  <── Validates DTO, HTTP status
     │ (Calls service method)
     ▼
[@Service UserService]           <── Business logic, Transaction boundary
     │ (Calls repository)
     ▼
[@Repository UserRepository]     <── Spring Data JPA / Hibernate
     │ (SQL execution)
     ▼
[Database (PostgreSQL / MySQL)]
```
