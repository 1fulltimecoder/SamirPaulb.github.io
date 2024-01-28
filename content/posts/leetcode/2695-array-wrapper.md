---
title: 2695 Array Wrapper
summary: 2695 Array Wrapper LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2695 Array Wrapper LeetCode Solution Explained in all languages", "2695 Array Wrapper", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2695 Array Wrapper - Solution Explained/problem-solving.webp
    alt: 2695 Array Wrapper
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2695. Array Wrapper](https://leetcode.com/problems/array-wrapper)


## Description

<p>Create a class&nbsp;<code>ArrayWrapper</code> that accepts&nbsp;an array of integers in its constructor. This class should have two features:</p>

<ul>
	<li>When two instances of this class are added together with the&nbsp;<code>+</code>&nbsp;operator, the resulting value is the sum of all the elements in&nbsp;both arrays.</li>
	<li>When the&nbsp;<code>String()</code>&nbsp;function is called on the instance, it will return a comma separated string surrounded by brackets. For example, <code>[1,2,3]</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [[1,2],[3,4]], operation = &quot;Add&quot;
<strong>Output:</strong> 10
<strong>Explanation:</strong>
const obj1 = new ArrayWrapper([1,2]);
const obj2 = new ArrayWrapper([3,4]);
obj1 + obj2; // 10
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [[23,98,42,70]], operation = &quot;String&quot;
<strong>Output:</strong> &quot;[23,98,42,70]&quot;
<strong>Explanation:</strong>
const obj = new ArrayWrapper([23,98,42,70]);
String(obj); // &quot;[23,98,42,70]&quot;
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [[],[]], operation = &quot;Add&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong>
const obj1 = new ArrayWrapper([]);
const obj2 = new ArrayWrapper([]);
obj1 + obj2; // 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>0 &lt;= nums[i]&nbsp;&lt;= 1000</code></li>
	<li><code>Note: nums is the array passed to the constructor</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```ts
class ArrayWrapper {
    private nums: number[];
    private s: number;

    constructor(nums: number[]) {
        this.nums = nums;
        this.s = nums.reduce((a, b) => a + b, 0);
    }

    valueOf() {
        return this.s;
    }

    toString() {
        return `[${this.nums}]`;
    }
}

/**
 * const obj1 = new ArrayWrapper([1,2]);
 * const obj2 = new ArrayWrapper([3,4]);
 * obj1 + obj2; // 10
 * String(obj1); // "[1,2]"
 * String(obj2); // "[3,4]"
 */
```

<!-- tabs:end -->

<!-- end -->