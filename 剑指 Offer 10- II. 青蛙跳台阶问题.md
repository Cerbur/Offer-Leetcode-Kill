# 剑指 Offer 10- II. 青蛙跳台阶问题

- https://leetcode-cn.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/

## 题目

![](https://raw.githubusercontent.com/Cerbur/pic/main/20210724013552.png)

## 解题思路

关于这题目，其实可以理解为当n <= 时候，n = 0，1能有1种跳法，n >= 2的时候能有跳一步和跳两步。而这时候跳1步后有多少解法就变成了n - 1有多少种解法，同样跳两步就变成了n - 2有多少种解法，存在重叠子问题，存在状态转移使用 dp，而状态转移方程为

```
F(N) = 1                           ( N <  2)
F(N) = F(N - 1) + F(N - 2)         ( N >= 2)
```

状态转移方程的意思是 n 个台阶有多少种结等于 跳一步后的解法 + 跳两步后的解法。

```java
class Solution {
    public int numWays(int n) {
        if (n < 2) {
            return 1;
        }
        int[] arr = new int[n + 1];
        arr[0] = 1;
        arr[1] = 1;
        for (int i = 2; i < n+1; i++) {
            arr[i] = (arr[i - 1] + arr[i - 2]) % 1000000007;
        }
        return arr[n];
    }
}
```

