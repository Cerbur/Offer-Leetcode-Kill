# 剑指 Offer 11. 旋转数组的最小数字

- https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/

## 题目

## 解题思路

这里我想复杂了只能贴个代码了，没什么值得参考的意义。

```java
class Solution {
    // 5 1 2 3 4
    // 1 2 3 4 5
    // 3 4 5 1 2
    public int minArray(int[] numbers) {
        int left = 0;
        int right = numbers.length - 1;
        
        while (left <= right) {
            if (right - left <= 1) {
                return Math.min(numbers[left],numbers[right]);
            }
            int mid = (left + right) / 2;
            if (numbers[left] < numbers[mid] && numbers[mid] < numbers[right]) {
                return numbers[left];
            } else if (numbers[left] < numbers[mid] && numbers[mid] > numbers[right]) {
                left  = mid;
            } else if (numbers[left] > numbers[mid] && numbers[mid] < numbers[right]) {
                right = mid;
            } else if (numbers[left] == numbers[mid]){
                left++;
            } else if (numbers[right] == numbers[mid]) {
                right--;
            }
        }
        return -1;
    }
}
```

下面贴一个官方的解题，解释写注释里

```java
class Solution {
    public int minArray(int[] numbers) {
        int low = 0;
        int high = numbers.length - 1;
        while (low < high) {
            int pivot = low + (high - low) / 2;
            if (numbers[pivot] < numbers[high]) {
              	// 如果中点小于右端点，说明数据肯定不在右边。
              	// 因为根据数据是被贴在右端说明右边区间是自增的
              	// 那右边的区间除去左端点，不可能是最低点。
              	// 1 2 3 4 5
              	// 5 1 2 3 4
                high = pivot;
            } else if (numbers[pivot] > numbers[high]) {
              // 当中点大于右端点的时候，说明右端区间存在一个从最小值自增的区间
                low = pivot + 1;
            } else {
                high -= 1;
            }
        }
        return numbers[low];
    }
}
```

作者：LeetCode-Solution
链接：https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/solution/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-by-leetcode-s/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。