# [面试题 08.01\. 三步问题](https://leetcode-cn.com/problems/three-steps-problem-lcci/)

Difficulty: **简单**

三步问题。有个小孩正在上楼梯，楼梯有n阶台阶，小孩一次可以上1阶、2阶或3阶。实现一种方法，计算小孩有多少种上楼梯的方式。结果可能很大，你需要对结果模1000000007。

**示例1:**

```
 输入：n = 3 
 输出：4
 说明: 有四种走法
```

**示例2:**

```
 输入：n = 5
 输出：13
```

**提示:**

1.  n范围在[1, 1000000]之间


## 题解

### 题解一：递归

```java
class Solution {
    int[] memory = new int[1000001];
    public int waysToStep(int n) {
        if (n == 1) {
            return 1;
        }
        if (n == 2) {
            return 2;
        }
        if (n == 3) {
            return 4;
        }
        if (memory[n] != 0) {
            return memory[n];
        }
        memory[n] = ((waysToStep(n - 1) + waysToStep(n - 2)) % 1000000007 + waysToStep(n - 3)) % 1000000007;
        return memory[n];
    }
}
```

#### 复杂度分析

- 时间复杂度：

- 空间复杂度：
