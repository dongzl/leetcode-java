### [面试题 17.10\. 主要元素](https://leetcode-cn.com/problems/find-majority-element-lcci/)

Difficulty: **简单**


数组中占比超过一半的元素称之为主要元素。给定一个**整数**数组，找到它的主要元素。若没有，返回-1。

**示例 1：**

```
输入：[1,2,5,9,5,9,5,5,5]
输出：5
```

**示例 2：**

```
输入：[3,2]
输出：-1
```

**示例 3：**

```
输入：[2,2,1,1,1,2,2]
输出：2
```

**说明：**  
你有办法在时间复杂度为 O(N)，空间复杂度为 O(1) 内完成吗？


## 题解

### 题解一：线性法 + 哈希

```java
class Solution {
    public int majorityElement(int[] nums) {
        int length = nums.length;
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < length; i++) {
            Integer count = map.getOrDefault(nums[i], 0);
            if (count + 1 > length / 2) {
                return nums[i];
            } else {
                map.put(nums[i], count + 1);
            }
        }
        return -1;
    }
}
```

#### 复杂度分析

- 时间复杂度：O(n)。

- 空间复杂度：O(n)。

### 题解二：摩尔投票法

```java
class Solution {
    public int majorityElement(int[] nums) {
        //判空
        if (nums.length == 0) {
            return -1;
        }

        //投票环节
        int major = 0;
        int vote = 0;
        for (int num : nums) {
            if (vote == 0) {
                major = num;
                vote++;
            } else {
                if (num == major) {
                    vote++;
                } else {
                    vote--;
                }
            }
        }
        
        //验证环节
        if (vote == 0) {
            return -1;
        }
        int identify = 0;
        for (int num : nums) {
            if (num == major) {
                identify++;
                if (identify > nums.length / 2) {
                    return major;
                }
            }
        }
        return -1;
    }
}
```

#### 复杂度分析

- 时间复杂度：O(n)

- 空间复杂度：O(1)
