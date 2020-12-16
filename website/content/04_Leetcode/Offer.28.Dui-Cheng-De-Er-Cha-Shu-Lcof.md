# [剑指 Offer 28\. 对称的二叉树](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)

Difficulty: **简单**

请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

```
    1  
   / \  
  2   2  
 / \ / \  
3  4 4  3
```  

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

```    
    1  
   / \  
  2   2  
   \   \  
   3    3
```

**示例 1：**

```
输入：root = [1,2,2,3,4,4,3]
输出：true
```

**示例 2：**

```
输入：root = [1,2,2,null,3,null,3]
输出：false
```

**限制：**

`0 <= 节点个数 <= 1000`

注意：本题与主站 101 题相同：


## 题解

### 题解一：递归

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
    public boolean isSymmetric(TreeNode root) {
        if (root == null) {
            return true;
        }
        return helper(root.left, root.right);
    }

    private boolean helper(TreeNode node1, TreeNode node2) {
        if (node1 == null && node2 == null) {
            return true;
        }
        if (node1 == null || node2 == null) {
            return false;
        }
        return node1.val == node2.val && helper(node1.left, node2.right) && helper(node1.right, node2.left);
    }
}
```

**复杂度分析**

- 时间复杂度：O(N)。

- 空间复杂度：O(N)，极端情况下退化为链表。
