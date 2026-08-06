# ⚡ Day 02 High-Yield Cheatsheet — OOP Principles & SQL Joins

## 🏛️ 1. OOP Principles Quick Reference
- **Encapsulation:** Data hiding & bundling (`private` fields + `public getters/setters`).
- **Abstraction:** Hiding implementation details (`interface` / `abstract class`).
- **Overloading vs Overriding:**
  - **Overloading:** Same method name, different parameters. *Compile-time polymorphism*.
  - **Overriding:** Same method name & signature in subclass. *Runtime polymorphism*.
- **Static Method Hiding:** `static` methods belong to the Class, not objects. Cannot be overridden. If redefined in subclass, it is **Method Hiding**, resolved by reference type at compile time.
- **Java 8 Interfaces:**
  - `default` methods: Concrete methods with body added for **backward compatibility**.
  - `static` methods: Utility functions called via `InterfaceName.methodName()`.

## 🔀 2. SQL Joins Cheat Table
| Join Type | Description | Unmatched Rows |
| :--- | :--- | :--- |
| `INNER JOIN` | Returns matching rows from both tables | Excluded |
| `LEFT JOIN` | Returns all rows from left table + matching from right | Right table columns padded with `NULL` |
| `SELF JOIN` | Joins table with itself (e.g. Employee vs Manager) | Alias table twice (`emp e JOIN emp m`) |

## 🧮 3. Key DSA Patterns
- **Integer Overflow (Reverse Integer):** Check `reverse > Integer.MAX_VALUE / 10` before `reverse * 10 + digit`.
- **Kadane's Recurrence:** $\text{currSum} = \max(\text{num}, \text{currSum} + \text{num})$
