# [剑指 Offer 25\. 合并两个排序的链表](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

Difficulty: **简单**

输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。

**示例1：**

```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```

**限制：**

`0 <= 链表长度 <= 1000`

注意：本题与主站 21 题相同：


## 题解

### 题解一：递归

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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if (l1 == null) {
            return l2;
        }
        if (l2 == null) {
            return l1;
        }
        if (l1.val < l2.val) {
            ListNode subHead = mergeTwoLists(l1.next, l2);
            l1.next = subHead;
            return l1;
        } else {
            ListNode subHead = mergeTwoLists(l1, l2.next);
            l2.next = subHead;
            return l2;
        }
    }
}
```

#### 复杂度分析

- 时间复杂度：

- 空间复杂度：
