# [面试题 04.03\. 特定深度节点链表](https://leetcode-cn.com/problems/list-of-depth-lcci/)

Difficulty: **中等**


给定一棵二叉树，设计一个算法，创建含有某一深度上所有节点的链表（比如，若一棵树的深度为 `D`，则会创建出 `D` 个链表）。返回一个包含所有深度的链表的数组。

**示例：**

```
输入：[1,2,3,4,5,null,7,8]

        1
       /  \ 
      2    3
     / \    \ 
    4   5    7
   /
  8

输出：[[1],[2,3],[4,5,7],[8]]
```


## 题解

### 题解一：BFS 二叉树层序遍历（Queue 数据结构）

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode[] listOfDepth(TreeNode tree) {
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(tree);
        List<ListNode> nodeList = new ArrayList<>();
        ListNode dummy = new ListNode(-1);
        while (!queue.isEmpty()) {
            int size = queue.size();
            ListNode currentNode = dummy;
            for (int i = 0; i < size; i++) {
                TreeNode current = queue.poll();
                currentNode.next = new ListNode(current.val);
                if (current.left != null) {
                    queue.add(current.left);
                }
                if (current.right != null) {
                    queue.add(current.right);
                }
                currentNode = currentNode.next;
            }
            nodeList.add(dummy.next);
        }
        return nodeList.toArray(new ListNode[]{});
    }
}
```
