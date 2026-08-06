# Day 02 Full Study & Revision Guide

## Module 1: Java OOP Principles

### 1. The 4 Pillars of Object-Oriented Programming

| Pillar | Definition | Real-World Example | Code Mechanism |
|---|---|---|---|
| **Abstraction** | Hiding implementation details and exposing only essential functionality. | Driving a car without knowing internal engine combustion. | `abstract class` & `interface` |
| **Encapsulation** | Wrapping data (variables) and methods together into a single unit and restricting direct access. | A capsule wrapping medicine inside a protective shell. | `private` variables + `public` getters/setters |
| **Inheritance** | Acquiring properties and behaviors of a parent class into a child class. | Child inheriting traits from parent. | `extends` keyword |
| **Polymorphism** | Ability of an object or method to take multiple forms. | A person acting as a customer, employee, or parent depending on context. | Method Overloading & Overriding |

---

### 2. Method Overloading vs Method Overriding

| Feature | Method Overloading | Method Overriding |
|---|---|---|
| **Type** | Compile-Time Polymorphism (Static Binding) | Runtime Polymorphism (Dynamic Binding) |
| **Location** | Within the **same class** | Between **Parent and Child class** |
| **Signature** | Same method name, **different parameter list** | Same method name, **exact same parameter list & return type** |
| **Private/Static Methods** | Can be overloaded | Cannot be overridden (static methods are hidden, not overridden) |

---

### 3. Abstract Class vs Interface (Java 8+)

| Feature | Abstract Class | Interface |
|---|---|---|
| **Methods** | Can have abstract & non-abstract methods | Abstract, `default`, `static`, and `private` methods |
| **State / Fields** | Can have instance variables | Only `public static final` constants |
| **Constructors** | Has constructors | Cannot have constructors |
| **Inheritance** | Single inheritance (`extends 1 class`) | Multiple inheritance (`implements multiple interfaces`) |

---

## Module 2: SQL Joins Master Class

### 1. Join Types Summary

```
INNER JOIN : Matches in both Table A AND Table B
LEFT JOIN  : All rows from Table A + matched rows from Table B (NULL if no match)
RIGHT JOIN : All rows from Table B + matched rows from Table A (NULL if no match)
FULL JOIN  : All rows from Table A AND Table B (NULL where no match exists)
SELF JOIN  : Joining Table A to Table A (Unary relationship, e.g., Employee-Manager)
```

### 2. Self Join Query Pattern (Employee-Manager)

```sql
-- Find employees who earn more than their direct manager
SELECT 
    e.name AS employee_name, 
    e.salary AS emp_salary, 
    m.name AS manager_name, 
    m.salary AS mgr_salary
FROM employees e
INNER JOIN employees m 
    ON e.manager_id = m.id
WHERE e.salary > m.salary;
```

---

## Module 3: Linked List Algorithms

### 1. Reverse a Singly Linked List ($O(N)$ Time, $O(1)$ Space)

```java
public ListNode reverseList(ListNode head) {
    ListNode prev = null;
    ListNode curr = head;
    
    while (curr != null) {
        ListNode nextTemp = curr.next; // Save next node
        curr.next = prev;              // Reverse pointer
        prev = curr;                   // Advance prev
        curr = nextTemp;               // Advance curr
    }
    
    return prev; // New head of reversed list
}
```

### 2. Floyd's Cycle Detection Algorithm ($O(N)$ Time, $O(1)$ Space)

```java
public boolean hasCycle(ListNode head) {
    if (head == null || head.next == null) return false;
    
    ListNode slow = head;
    ListNode fast = head;
    
    while (fast != null && fast.next != null) {
        slow = slow.next;          // Move 1 step
        fast = fast.next.next;     // Move 2 steps
        
        if (slow == fast) {
            return true; // Cycle detected
        }
    }
    
    return false; // Reached end, no cycle
}
```
