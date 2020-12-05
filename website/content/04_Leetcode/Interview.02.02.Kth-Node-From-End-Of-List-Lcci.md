# [面试题 02.02\. 返回倒数第 k 个节点](https://leetcode-cn.com/problems/kth-node-from-end-of-list-lcci/)

Difficulty: **简单**


实现一种算法，找出单向链表中倒数第 k 个节点。返回该节点的值。

**注意：**本题相对原题稍作改动

**示例：**

```shell
输入： 1->2->3->4->5 和 k = 2
输出： 4
```

**说明：**

给定的 _k_ 保证是有效的。


## 题解

### 题解一：

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public int kthToLast(ListNode head, int k) {
        int length = 0;
        ListNode temp = head;
        while (temp != null) {
            length++;
            temp = temp.next;
        }
        for (int i = 0; i < length - k; i++) {
            head = head.next;
        }
        return head.val;
    }
}
```

#### 复杂度分析

- 时间复杂度：O(n)。

- 空间复杂度：O(1)。
