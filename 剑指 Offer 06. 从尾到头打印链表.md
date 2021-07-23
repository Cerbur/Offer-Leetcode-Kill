# 剑指 Offer 06. 从尾到头打印链表

- https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/

反正我写的很骚

## 题目

![](https://raw.githubusercontent.com/Cerbur/pic/main/20210724045415.png)

## 解题思路

利用函数自身来压栈

```java
class Solution {
    int[] res;
    int count = 0;
    int k = 0;
    public int[] reversePrint(ListNode head) {
        back(head);
        return res;
    }

    void back(ListNode head) {
        if (head != null) {    
            count ++;
            reversePrint(head.next);            
        } else {
            res = new int[count];
            return;
        }
        res[k++] = head.val;
    }
}
```

