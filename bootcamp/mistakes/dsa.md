# DSA Mistakes

| Topic | Date | Mistake | Root Cause | Correct Approach | Frequency | Revision Required |
|---|---|---|---|---|---:|---|
| Kadane's Algorithm | 2026-08-04 | Skipped formal $O(N)$ proof & implementation during drill | Focused heavily on theory without writing subarray DP logic | Use dynamic greedy scan: `currentSum = max(arr[i], currentSum + arr[i])` and `maxSum = max(maxSum, currentSum)` | 1 | Yes |
