# [面试题 04.05\. 合法二叉搜索树](https://leetcode-cn.com/problems/legal-binary-search-tree-lcci/)

Difficulty: **中等**


实现一个函数，检查一棵二叉树是否为二叉搜索树。

**示例 1:**

```
输入:    2   / \  1   3输出: true
```

**示例 2:**

```
输入:    5   / \  1   4     / \    3   6输出: false解释: 输入为: [5,1,4,null,null,3,6]。     根节点的值为 5 ，但是其右子节点值为 4 。
```


## 题解

### 题解一：BSF 遍历（Stack 数据结构）

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
    public boolean isValidBST(TreeNode root) {
    	Stack<TreeNode> stack = new Stack<TreeNode>();
        Integer currValue = null;
        TreeNode curr = root;
        while (curr != null || !stack.isEmpty()) {
            if (curr != null) {
                stack.push(curr);
                curr = curr.left;
            } else {
                curr = stack.pop();
                if (currValue != null && curr.val <= currValue) {
                    return false;
                }
                currValue = curr.val;
                curr = curr.right;
            }
        }
        return true;
    }
}
```

### 题解二：递归求解

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
    public boolean isValidBST(TreeNode root) {
    	return isValidBST(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }

	private boolean isValidBST(TreeNode root, long min, long max) {
		return root == null || (root.val > min && root.val < max && 
             isValidBST(root.left, min, root.val) && 
             isValidBST(root.right, root.val, max));
	}
}
```
