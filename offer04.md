# 剑指offer04.二维数组中的查找

https://leetcode-cn.com/problems/substring-with-concatenation-of-all-words/



### 题目说明

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。



**示例**：

现有矩阵 matrix 如下：

[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。

给定 target = 20，返回 false。



### 解答

**思路**： 

线性查找，观察发现，右上角或左下角的元素具有特点。以右上角为例，向左元素减小，向下元素增大。



### 方法1 

时间复杂度 O(m+n) 空间复杂度O(1)

从右上角开始线性查找，大于目标，向左移动减小，小于目标向下移动增大

```java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        // 特殊情况处理
        if(matrix == null) return false;
        // n为行
        int n = matrix.length;
        if(n == 0) return false;
        // m为列
        int m = matrix[0].length;
        if(m == 0) return false;
        
        int x = 0;
        int y = m - 1;
        while(x < n && y >= 0) {
            if(target == matrix[x][y]) return true;
            else if(target > matrix[x][y]) x++;
            else y--;
        }
        return false;

    }
}
```







