# [面试题 10.01\. 合并排序的数组](https://leetcode-cn.com/problems/sorted-merge-lcci/)

Difficulty: **简单**

给定两个排序后的数组 A 和 B，其中 A 的末端有足够的缓冲空间容纳 B。 编写一个方法，将 B 合并入 A 并排序。

初始化 A 和 B 的元素数量分别为 _m_ 和 _n_。

**示例:**

```
输入:
A = [1,2,3,0,0,0], m = 3
B = [2,5,6],       n = 3

输出: [1,2,2,3,5,6]
```

**说明:**

*   `A.length == n + m`


## 题解

### 题解一：暴力法

```java
class Solution {
    public void merge(int[] A, int m, int[] B, int n) {
        for (int i = 0; i != n; ++i) {
            A[m + i] = B[i];
        }
        Arrays.sort(A);
    }
}
```

#### 复杂度分析

- 时间复杂度：

- 空间复杂度：
