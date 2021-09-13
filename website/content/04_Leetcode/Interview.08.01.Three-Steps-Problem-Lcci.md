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
    public int waysToStep(int n) {
        int[] Step = {1, 2, 4};
        for(int i = 3; i < n; i++){
            Step[i % 3] = ((Step[0] + Step[1]) % 1000000007 + Step[2]) % 1000000007;
        }
        return Step[(n-1) % 3];
    }
}
```

#### 复杂度分析

- 时间复杂度：

- 空间复杂度：
