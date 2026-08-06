# Common Mistakes Log

Use this format for every repeated mistake.

| Topic | Date | Mistake | Root Cause | Correct Approach | Frequency | Revision Required |
|---|---|---|---|---|---:|---|
| Java String Pool | 2026-08-04 | Confused object creation count for `new String("CDAC")` | Didn't separate Heap object allocation from SCP literal check | `new String("CDAC")` creates 2 objects if literal isn't in SCP (1 Heap, 1 SCP), or 1 Heap object if literal already exists in SCP | 1 | Yes |
| Kadane's Algorithm | 2026-08-04 | Skipped formal $O(N)$ proof & implementation during drill | Focused heavily on theory without writing subarray DP logic | Use dynamic greedy scan: `currentSum = max(arr[i], currentSum + arr[i])` and `maxSum = max(maxSum, currentSum)` | 1 | Yes |
