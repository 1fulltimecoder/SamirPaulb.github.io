---
title: 0254 Factor Combinations
summary: 0254 Factor Combinations LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0254 Factor Combinations LeetCode Solution Explained in all languages", "0254 Factor Combinations", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0254 Factor Combinations - Solution Explained/problem-solving.webp
    alt: 0254 Factor Combinations
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [254. Factor Combinations](https://leetcode.com/problems/factor-combinations)


## Description

<p>Numbers can be regarded as the product of their factors.</p>

<ul>
	<li>For example, <code>8 = 2 x 2 x 2 = 2 x 4</code>.</li>
</ul>

<p>Given an integer <code>n</code>, return <em>all possible combinations of its factors</em>. You may return the answer in <strong>any order</strong>.</p>

<p><strong>Note</strong> that the factors should be in the range <code>[2, n - 1]</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> []
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 12
<strong>Output:</strong> [[2,6],[3,4],[2,2,3]]
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 37
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>7</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def getFactors(self, n: int) -> List[List[int]]:
        def dfs(n, i):
            if t:
                ans.append(t + [n])
            j = i
            while j * j <= n:
                if n % j == 0:
                    t.append(j)
                    dfs(n // j, j)
                    t.pop()
                j += 1

        t = []
        ans = []
        dfs(n, 2)
        return ans
```

```java
class Solution {
    private List<Integer> t = new ArrayList<>();
    private List<List<Integer>> ans = new ArrayList<>();

    public List<List<Integer>> getFactors(int n) {
        dfs(n, 2);
        return ans;
    }

    private void dfs(int n, int i) {
        if (!t.isEmpty()) {
            List<Integer> cp = new ArrayList<>(t);
            cp.add(n);
            ans.add(cp);
        }
        for (int j = i; j <= n / j; ++j) {
            if (n % j == 0) {
                t.add(j);
                dfs(n / j, j);
                t.remove(t.size() - 1);
            }
        }
    }
}
```

```cpp
class Solution {
public:
    vector<vector<int>> getFactors(int n) {
        vector<int> t;
        vector<vector<int>> ans;
        function<void(int, int)> dfs = [&](int n, int i) {
            if (t.size()) {
                vector<int> cp = t;
                cp.emplace_back(n);
                ans.emplace_back(cp);
            }
            for (int j = i; j <= n / j; ++j) {
                if (n % j == 0) {
                    t.emplace_back(j);
                    dfs(n / j, j);
                    t.pop_back();
                }
            }
        };
        dfs(n, 2);
        return ans;
    }
};
```

```go
func getFactors(n int) [][]int {
	t := []int{}
	ans := [][]int{}
	var dfs func(n, i int)
	dfs = func(n, i int) {
		if len(t) > 0 {
			ans = append(ans, append(slices.Clone(t), n))
		}
		for j := i; j <= n/j; j++ {
			if n%j == 0 {
				t = append(t, j)
				dfs(n/j, j)
				t = t[:len(t)-1]
			}
		}
	}
	dfs(n, 2)
	return ans
}
```

<!-- tabs:end -->

<!-- end -->