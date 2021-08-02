## Problem Statement

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Example 1:**

```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

**Example 2:**

```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step

```

**Constraints:**

```
1 <= n <= 45
```

## Solution

**Approach (using DP)**

Let's do the bottom-up approach.

**Base Case**

1. for step 0 it there is only 1 way (i.e to stand).
2. for step 1 there is only 1 way.

```
int climbStairs(int n) {
        int memo[n+1];
        memo[0] = 1;
        memo[1] = 1;
        for(int i = 2 ; i <= n ; i++){
            memo[i] = memo[i-1] + memo[i-2];
        }
        return memo[n];
    }
```

Reference : [leetcodeProblem](https://leetcode.com/problems/climbing-stairs/)
