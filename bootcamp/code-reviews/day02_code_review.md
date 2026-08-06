# 🔍 Day 02 Code Review — LeetCode & SQL Queries

## 1. LeetCode #7 — Reverse Integer (Medium)
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
* **Time Complexity:** $\mathcal{O}(\log_{10}(N))$
* **Space Complexity:** $\mathcal{O}(1)$
* **Review Verdict:** **PASS (10/10)** — Flawless 32-bit signed integer overflow protection without using 64-bit `long` types.

## 2. SQL Self Join Query Review
```sql
SELECT e.ename AS employee, e.sal AS employee_sal, m.ename AS manager, m.sal AS manager_sal
FROM emp e
JOIN emp m ON e.mgr = m.empno
WHERE e.sal > m.sal;
```
* **Review Verdict:** **PASS (10/10)** — Precise table aliased self-join matching `e.mgr = m.empno` with clear column aliases.
