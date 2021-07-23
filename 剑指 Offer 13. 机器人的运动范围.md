# 剑指 Offer 13. 机器人的运动范围

- https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/

这是一题很好的广度优先搜索的模版题

## 题目

![](https://raw.githubusercontent.com/Cerbur/pic/main/20210724043542.png)

## 解题笔记

模版 

定义 队列，二维数组，way数组

循环数字出队、向四个方向校验合法性、合法加入队列中

处理对应逻辑，比如说加值。

```java
class Solution {
    public int movingCount(int m, int n, int k) {
        Queue<int[]> queue = new ArrayDeque();
        boolean[][] visited = new boolean[m][n];
        queue.add(new int[]{0,0});
        visited[0][0] = true;
        int count = 1;
        int[][] way = new int[][]{
            {1,0},
            {-1,0},
            {0,1},
            {0,-1}
            };
        while(!queue.isEmpty()) {
            int[] q = queue.poll();
            for (int i = 0;i < way.length;i++) {
                int x = q[0] + way[i][0];
                int y = q[1] + way[i][1];
                if ( x < 0 || x >= m || y < 0 || 
                    y >= n || getCount(x,y) > k || visited[x][y]) {
                    continue;
                }
                visited[x][y] = true;
                queue.add(new int[]{x,y});
                count ++;
            }
            
        }
        return count;
    }
    int getCount(int x, int y) {
        int count = 0;
        while (x != 0 || y != 0) {
            count += x %10;
            count += y %10;
            y /= 10;
            x /= 10;
        }
        return count;
    }
}
```

