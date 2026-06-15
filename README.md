# 560. Subarray Sum Equals K (Brute Force)

## Problem Statement

Given an integer array `nums` and an integer `k`, return the total number of continuous subarrays whose sum equals `k`.

A subarray is a contiguous non-empty sequence of elements within an array.

### Example 1

Input:

```text
nums = [1,1,1]
k = 2
```

Output:

```text
2
```

### Example 2

Input:

```text
nums = [1,2,3]
k = 3
```

Output:

```text
2
```

---

## Brute Force Approach

The idea is to generate every possible subarray and calculate its sum.

For each starting index:

1. Initialize `sum = 0`.
2. Extend the subarray one element at a time.
3. Add the current element to `sum`.
4. If `sum == k`, increment the count.

Instead of recalculating the sum of every subarray from scratch, we maintain a running sum while expanding the subarray.

---

## Dry Run

### Input

```text
nums = [1,1,1]
k = 2
```

### Iteration 1

Start at index `0`

```text
[1]       sum = 1
[1,1]     sum = 2  ✓
[1,1,1]   sum = 3
```

Count = 1

### Iteration 2

Start at index `1`

```text
[1]       sum = 1
[1,1]     sum = 2  ✓
```

Count = 2

### Iteration 3

Start at index `2`

```text
[1]       sum = 1
```

Final Count:

```text
2
```

---

## Algorithm

1. Initialize `count = 0`.
2. Loop through each index as the starting point.
3. Maintain a running sum.
4. Extend the subarray to the right.
5. Whenever the running sum equals `k`, increment the count.
6. Return the count.

---

## Java Solution

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            int sum = 0;

            for (int j = i; j < nums.length; j++) {
                sum += nums[j];

                if (sum == k) {
                    count++;
                }
            }
        }

        return count;
    }
}
```

---

## Complexity Analysis

### Time Complexity

```text
O(n²)
```

There are `n` starting positions, and for each position we may traverse up to `n` elements.

### Space Complexity

```text
O(1)
```

Only a few extra variables are used.

---

## Key Takeaway

The brute-force solution checks every possible subarray using two nested loops and a running sum. While simple to understand and implement, it takes `O(n²)` time and can be optimized to `O(n)` using the Prefix Sum + HashMap approach.
