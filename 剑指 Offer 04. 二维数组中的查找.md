# 剑指 Offer 04. 二维数组中的查找

- https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/

## 题目

![](https://raw.githubusercontent.com/Cerbur/pic/main/20210724011505.png)



## 解题笔记

我们可以知道数据从上到下是逐渐增大的，从左到右也是逐渐增大的。也就是，其实我们的数据是一个斜面。对于二分法，我们知道我们其实是在做，左右两个指针从不同方向逼进的。左指针从小数据向大数据逼进，右指针从大数据向小数据逼进，左右指针是沿着数据的两个方向移动的。

那么回到这题，我们需要从端点选择我们要逼进的数据。我们可以选择左上、右上、左下、右下四个点进行逼进。当我们的数据是在左上的时候，x 和 y 如果用简单的方法看，只能沿着数据增大的方向逼进。而同样的右下角的点也是只能向数据减小的方向逼进。

当我们选择左下、右下的点的时候。x 和 y 的运动就可以沿着一个增加、另一个减小的方向运动了。所以我们从左下的点出发。当这个数据大于我们的数据时候，我们就向数据减小的方向移动，也就是 x 减小，当这个数据小于我们要的数据的时候，向数据增大的方向移动，也就是 y 增大。可得到下面代码。

```java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        int row = matrix.length;
        if (row == 0) {
            return false;
        }
        int col = matrix[0].length;

        int x = row - 1;
        int y = 0;
        while (x >= 0 && y < col) {
            int num = matrix[x][y];
            if ( num == target ) {
                return true;
            } else if (num > target) {
                x --;
            } else {
                y ++;
            }
        }
        return false;
    }
}
```

