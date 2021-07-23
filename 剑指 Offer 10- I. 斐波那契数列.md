# 剑指 Offer 10- I. 斐波那契数列

- https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/

## 题目

![](https://raw.githubusercontent.com/Cerbur/pic/main/20210723172344.png)

## 解答笔记

本质是一个dp，F(N) = F(N - 1) + F(N - 2), 其中 N > 1。就是这个dp问题的状态转移方程。

注意读题取模。

```java
class Solution {
    public int fib(int n) {
        int[] a = new int[n+1];
        if (n < 2) {
            return n;
        }
        a[0] = 0;
        a[1] = 1;
        for (int i = 2; i < n + 1; i++) {
            a[i] = a[i - 1] + a[i -2];
            a[i] %= 1000000007;
        }
        return a[n];
   }
}
```

