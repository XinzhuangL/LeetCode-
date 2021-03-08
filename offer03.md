# 剑指offer03.数组中重复的数字

https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/



### 题目说明

找出数组中重复的数字。

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

**示例1**：

```java
输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 
```



### 解答

**思路**：原地置换，如果没有重复数字，那么正常排序以后，数字i应该在下标为i的位置，我们从头扫描数组，遇到下标i的数字不为i的话，假设为m，我们就与下标m的数字交换。交换过程中如果有重复的数字，终止返回



### 方法1 

时间复杂度 O(n) 空间复杂度O(1)

```java
class Solution {
  public int findRepeatNumber(int[] nums) {
    int temp;
    for(int i = 0; i < nums.length; i++) {
      while(nums[i] != i) {
        // 代表有重复数据
        if(nums[i] == nums[nums[i]]) {
          return nums[i];
        }
        temp = nums[i];
        nums[i] = nums[temp];
        nums[temp] = temp;
      }
    }
    return -1;
  }
}
```





