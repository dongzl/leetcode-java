# [面试题 08.05\. 递归乘法](https://leetcode-cn.com/problems/recursive-mulitply-lcci/)

Difficulty: **中等**

递归乘法。 写一个递归函数，不使用 * 运算符， 实现两个正整数的相乘。可以使用加号、减号、位移，但要吝啬一些。

**示例1:**

```
 输入：A = 1, B = 10
 输出：10
```

**示例2:**

```
 输入：A = 3, B = 4
 输出：12
```

**提示:**

1.  保证乘法范围不会溢出


## 题解

### 题解一：递归

```java
class Solution {
    public int multiply(int A, int B) {
        if (B == 1) {
            return A;
        }
        int half = multiply(A, B / 2);
        if (B % 2 == 1) {
            return half + half + A;
        } else {
            return half + half;
        }
    }
}
```

#### 复杂度分析

- 时间复杂度：

- 空间复杂度：
