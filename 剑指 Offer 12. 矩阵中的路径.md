# 剑指 Offer 12. 矩阵中的路径

- https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof/

这题目我得重点多看几次，走格子很重要的一个模版。

## 题目

![](https://raw.githubusercontent.com/Cerbur/pic/main/20210724035704.png)

## 解答笔记

这题我开始思路就错了，我选择了用bfs，最后发现应该用dfs的时候心态有点差了。

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        for (int i = 0; i < board.length; i ++) {
            for (int j = 0; j < board[0].length; j++) {
                if (board[i][j] == word.charAt(0) && dfs(board, i,j,0,word)) {
                    return true;
                }
            }
        }
        return false;
    }
    boolean dfs(char[][] board, int x, int y, int count, String word) {
        if (x < 0 || x >= board.length 
        || y < 0 || y >= board[0].length 
        || board[x][y] != word.charAt(count)) {
            return false;
        }
        if (count == word.length() - 1) {
            return true;
        }
      	// 选择
        board[x][y] = '\0';
        boolean res = dfs(board,x + 1,y,count + 1,word) ||
                    dfs(board,x - 1,y,count + 1,word) ||
                    dfs(board,x ,y + 1,count + 1,word) ||
                    dfs(board,x ,y - 1,count + 1,word);
      	// 取消选择
        board[x][y] = word.charAt(count);
        return res;
    }
}
```

