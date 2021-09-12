# [剑指 Offer 10- II. 青蛙跳台阶问题](https://leetcode-cn.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/)

Difficulty: **简单**

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 `n` 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

**示例 1：**

```
输入：n = 2
输出：2
```

**示例 2：**

```
输入：n = 7
输出：21
```

**示例 3：**

```
输入：n = 0
输出：1
```

**提示：**

*   `0 <= n <= 100`

注意：本题与主站 70 题相同：


## 题解

### 题解一：递归

```java
class Solution {
    Map<Integer, Integer> map = new HashMap<Integer, Integer>();
    public int numWays(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        if (map.containsKey(n)) {
            return map.get(n);
        }
        int result = (numWays(n - 1) + numWays(n - 2)) % 1000000007;
        map.put(n, result);
        return result;
    }
}
```

#### 复杂度分析

- 时间复杂度：

- 空间复杂度：
