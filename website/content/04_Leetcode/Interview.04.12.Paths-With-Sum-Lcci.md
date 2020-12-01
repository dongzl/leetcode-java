# [面试题 04.12\. 求和路径](https://leetcode-cn.com/problems/paths-with-sum-lcci/)

Difficulty: **中等**


给定一棵二叉树，其中每个节点都含有一个整数数值(该值或正或负)。设计一个算法，打印节点数值总和等于某个给定值的所有路径的数量。注意，路径不一定非得从二叉树的根节点或叶节点开始或结束，但是其方向必须向下(只能从父节点指向子节点方向)。

**示例:**  
给定如下二叉树，以及目标和 `sum = 22`，

```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
```

返回:

```
3
解释：和为 22 的路径有：[5,4,11,2], [5,8,4,5], [4,11,7]
```

提示：

*   `节点总数 <= 10000`


## 题解

### 题解一：BSF + DFS（BSF 使用 Queue 数据结构）

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
class Solution {

    private int result;

    public int pathSum(TreeNode root, int sum) {
        if (root == null) {
            return 0;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while (!queue.isEmpty()) {
            TreeNode currentNode = queue.poll();
            helper(currentNode, sum, 0);
            if (currentNode.left != null) {
                queue.add(currentNode.left);
            }
            if (currentNode.right != null) {
                queue.add(currentNode.right);
            }
        }
        return result;
    }

    private void helper(TreeNode node, int sum, int currentSum) {
        if (node == null) {
            return;
        }
        currentSum += node.val;
        if (currentSum == sum) {
            result++;
        }
        helper(node.left, sum, currentSum);
        helper(node.right, sum, currentSum);
    }
}
```
