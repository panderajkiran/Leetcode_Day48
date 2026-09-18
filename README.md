# Leetcode_Day48
# Day 48 — Best Time to Buy and Sell Stock III

**LeetCode Problem:** 123. Best Time to Buy and Sell Stock III  
**Difficulty:** Hard  
**Language:** Java

## Problem

You are given an array `prices` where `prices[i]` represents the stock price on the `i-th` day.

You can complete **at most two transactions**.

A transaction means:
- Buy one stock
- Sell it later
- Then you can buy again

You cannot hold multiple stocks at the same time.

### Example

```text
Input:
prices = [3,3,5,0,0,3,1,4]

One possible way:

First transaction:
Buy at 0 → Sell at 3 = Profit 3

Second transaction:
Buy at 1 → Sell at 4 = Profit 3

Total Profit = 6
```
Approach

I used a 4-state greedy/dynamic programming approach.

We maintain:

buy1 → minimum price for the first purchase
profit1 → maximum profit after the first sale
buy2 → effective cost of the second purchase after considering the first profit
profit2 → maximum profit after the second sale

For every price:

buy1 = Math.min(buy1, price);
profit1 = Math.max(profit1, price - buy1);

buy2 = Math.min(buy2, price - profit1);
profit2 = Math.max(profit2, price - buy2);

At the end, profit2 contains the maximum profit possible using at most two transactions.

Why This Works

Instead of checking every possible pair of transactions, we continuously keep track of the best result for each stage.

First Buy → First Sell → Second Buy → Second Sell

Each new price updates these four states and keeps the best value found so far.

This allows the entire array to be processed only once.

Complexity
Time Complexity: O(n)
Space Complexity: O(1)

Where n is the number of prices.

What I Learned

Today I learned how multiple stock transactions can be handled by maintaining a small number of states instead of trying every possible combination.

The important idea was understanding that the second transaction can use the profit earned from the first transaction.

Key Takeaway

Sometimes a difficult problem becomes manageable when you stop looking at all possible combinations and instead track only the few states that actually matter.

Output:
6
