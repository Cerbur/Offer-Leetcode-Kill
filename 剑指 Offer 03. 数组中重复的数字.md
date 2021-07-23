# 剑指 Offer 03. 数组中重复的数字

https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/

## 题目

![](https://raw.githubusercontent.com/Cerbur/pic/main/20210723172524.png)

## 解答笔记

这里用到一个Set来记录旧的值，考察的是对Set的运用场景。

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int num :nums) {
            if (set.contains(num)) {
                return num;
            }
            set.add(num);
        }
        return -1;
    }
}
```



由于题目限制了数据的大小，可以实现说数据与下标一一对应，如果出现下标和数据一致就移步，如果不一致就看下标数据是否相等，相等就说明出现过，返回即可，不相等就交换到相等。是个O1空间 On时间到解法。

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        int i = 0;
        while(i < nums.length) {
            if(nums[i] == i) {
                i++;
                continue;
            }
            if(nums[nums[i]] == nums[i]) return nums[i];
            int tmp = nums[i];
            nums[i] = nums[tmp];
            nums[tmp] = tmp;
        }
        return -1;
    }
}
```

