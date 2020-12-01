# [剑指 Offer 32 - II. 从上到下打印二叉树 II](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

Difficulty: **简单**


从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

例如:  
给定二叉树: `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

返回其层次遍历结果：

```
[
  [3],
  [9,20],
  [15,7]
]
```

**提示：**

1.  `节点总数 <= 1000`

注意：本题与主站 102 题相同：

## 题解

### 解法一：BFS 广度优先遍历（Queue 数据结构）

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> allResult = new ArrayList<>();
        if (root == null) {
            return allResult;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()) {
            int size = queue.size();
            List<Integer> result = new ArrayList<>();
            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                result.add(node.val);
                if (node.left != null) {
                    queue.add(node.left);
                }
                if (node.right != null) {
                    queue.add(node.right);
                }
            }
            allResult.add(result);
        }
        return allResult;
    }
}
```

### 解法二：DFS 深度优先遍历

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        helper(root, result, 0);
        return result;
    }

    private void helper(TreeNode node, List<List<Integer>> result, int level) {
        if (node == null) {
            return;
        }
        if (level >= result.size()) {
            result.add(new ArrayList<>());
        }
        result.get(level).add(node.val);
        helper(node.left, result, level + 1);
        helper(node.right, result, level + 1);
    }
}
```
