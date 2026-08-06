# Java Mistakes

| Topic | Date | Mistake | Root Cause | Correct Approach | Frequency | Revision Required |
|---|---|---|---|---|---:|---|
| String Constant Pool | 2026-08-04 | Confused object creation count for `new String("CDAC")` | Didn't separate Heap object allocation from SCP literal check | `new String("CDAC")` creates 2 objects if literal isn't in SCP (1 Heap, 1 SCP), or 1 Heap object if literal already exists in SCP | 1 | Yes |
