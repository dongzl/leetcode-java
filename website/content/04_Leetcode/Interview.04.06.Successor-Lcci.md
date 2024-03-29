# [面试题 04.06\. 后继者](https://leetcode-cn.com/problems/successor-lcci/)

Difficulty: **中等**

设计一个算法，找出二叉搜索树中指定节点的“下一个”节点（也即中序后继）。

如果指定节点没有对应的“下一个”节点，则返回`null`。

**示例 1:**

```
输入: root = [2,1,3], p = 1

  2
 / \
1   3

输出: 2
```

**示例 2:**

```
输入: root = [5,3,6,2,4,null,null,1], p = 6

      5
     / \
    3   6
   / \
  2   4
 /   
1

输出: null
```


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
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        List<TreeNode> list = new ArrayList<>();
        helper(root, list);
        for (int i = 0; i < list.size(); i++) {
            if (list.get(i).val == p.val && i < list.size() - 1) {
                return list.get(i + 1);
            }
        }
        return null;
    }

    private void helper(TreeNode node, List<TreeNode> list) {
        if (node == null) {
            return;
        }
        helper(node.left, list);
        list.add(node);
        helper(node.right, list);
    }
}
```

#### 复杂度分析

- 时间复杂度：

- 空间复杂度：
