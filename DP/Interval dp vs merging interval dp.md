# Difference Between Merging Intervals DP and Intervals DP

>Dynamic Programming (DP) involves solving complex problems by breaking them down into simpler subproblems and storing the results of these subproblems to avoid redundant computations. Two related but distinct patterns in DP that deal with intervals are **Merging Intervals DP** and **Intervals DP**. Here’s a detailed comparison between the two:

## Intervals DP

**Intervals DP** involves problems where the solution requires analyzing and optimizing intervals within a given range. The key aspect of Intervals DP is that you typically consider the properties of the intervals themselves rather than merging them.

### Key Characteristics
1. **Definition of Subproblems**: The subproblems are defined over intervals, usually represented by `dp[i][j]`, where you need to compute some property for the interval from `i` to `j`.
2. **Non-Merging**: The intervals are usually not merged but rather considered in their original form. The focus is on determining the optimal way to select or partition intervals.
3. **Transition**: The transition involves choosing optimal partitions or selections within an interval without explicitly merging them.

### Examples

1. **Longest Palindromic Subsequence**
   - **Problem**: Find the longest subsequence that is a palindrome within a given string.
   - **DP State**: `dp[i][j]` represents the length of the longest palindromic subsequence in the interval `[i, j]`.
   - **Transition**: Based on whether the characters at the ends of the interval match or not.

2. **Minimum Insertions to Form a Palindrome**
   - **Problem**: Find the minimum number of insertions needed to make a given string a palindrome.
   - **DP State**: `dp[i][j]` represents the minimum insertions needed for the interval `[i, j]` to become a palindrome.
   - **Transition**: Based on insertions required when characters at the ends don't match.

3. **Longest Common Subsequence (LCS)**
   - **Problem**: Find the longest common subsequence between two strings.
   - **DP State**: Often represented as `dp[i][j]` where `i` and `j` are indices in the two strings.
   - **Transition**: Based on characters matching or not and considering subproblems `dp[i-1][j]`, `dp[i][j-1]`, etc.

## Merging Intervals DP

**Merging Intervals DP** involves problems where you need to combine or merge intervals in some optimal way. The core idea is that the solution to the problem involves merging smaller intervals into larger ones.

### Key Characteristics
1. **Definition of Subproblems**: Similar to Intervals DP, subproblems are defined over intervals, typically `dp[i][j]`.
2. **Merging**: The primary operation is merging intervals. The focus is on determining the optimal way to combine intervals.
3. **Transition**: The transition involves merging the results of smaller intervals to form a larger interval.

### Examples

1. **Matrix Chain Multiplication**
   - **Problem**: Determine the optimal order to multiply a chain of matrices to minimize the number of scalar multiplications.
   - **DP State**: `dp[i][j]` represents the minimum number of multiplications needed to compute the product of matrices from index `i` to `j`.
   - **Transition**: `dp[i][j] = min(dp[i][k] + dp[k+1][j] + cost(i, k, j))` for all valid `k` in `[i, j-1]`.

2. **Burst Balloons (LeetCode 312)**
   - **Problem**: Given `n` balloons, each balloon has a number of coins. The goal is to burst all balloons to maximize the coins collected.
   - **DP State**: `dp[i][j]` represents the maximum coins collected by bursting balloons between indices `i` and `j`.
   - **Transition**: `dp[i][j] = max(dp[i][k-1] + dp[k+1][j] + nums[i-1]*nums[k]*nums[j+1])` for all `i <= k <= j`.

3. **Minimum Cost to Merge Stones**
   - **Problem**: Given an array of stones, merge them into one pile with the minimum cost.
   - **DP State**: `dp[i][j]` represents the minimum cost to merge stones from index `i` to `j`.
   - **Transition**: `dp[i][j] = min(dp[i][k] + dp[k+1][j] + sum(i, j))` for all `i <= k < j`.

## Summary

- **Intervals DP**:
  - Focuses on properties or selections within intervals.
  - Typically involves partitioning or optimizing within the interval without merging.
  - Example problems include Longest Palindromic Subsequence and Longest Common Subsequence.

- **Merging Intervals DP**:
  - Focuses on merging smaller intervals to form larger intervals optimally.
  - The primary operation involves combining intervals.
  - Example problems include Matrix Chain Multiplication and Burst Balloons.

Understanding the difference helps in identifying the right approach and state transitions when faced with a new DP problem involving intervals.
