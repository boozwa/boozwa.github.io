---
title: "Dyanmic Programming - Example 1"
date: 2020-09-18T15:34:30-04:00
excerpt: "Dyanmic Programming - Example 1: Fibonacci Numbers"
categories:
  - programing
tags:
  - javascript
  - coding
  - dynamic programming
share: true
---

I want to learn more about dynamic programming and found this **AWESOME** post on [Medium][medium-post]. 

Example 1: Fibonacci Numbers

To calculate F(n) for a giving n:

{%highlight javascript %}
    function solveTopDown(n, memo) {
    if (memo[n]) return memo[n];
    const result = solveTopDown(n - 1, memo) + solveTopDown(n - 2, memo);
    memo[n] = result;
    return result;
    }

    function topDown(n) {
    return solveTopDown(n, { 1: 1, 2: 1 });
    }

    function bottomUp(n) {
    const memo = [0, 1, 1];
    for (let i = 3; i <= n; i++) {
        memo[i] = memo[i - 1] + memo[i - 2];
    }
    return memo[n];
    }

    let i = 0;
    while(i++ < 100) {
    const topDownResult = topDown(i);
    const bottomUpResult = bottomUp(i);
    if (topDownResult !== bottomUpResult) {
        throw new Error('Your algorithm is bad, break at ', i);
    }
    console.log(`F(${i})=${topDownResult}`);
    }
{% endhighlight %}

[medium-post]: https://medium.com/@davidguandev/introduction-to-dynamic-programming-with-examples-bc04dca3ccee