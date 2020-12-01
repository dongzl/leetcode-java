# [剑指 Offer 54\. 二叉搜索树的第k大节点](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

Difficulty: **简单**


给定一棵二叉搜索树，请找出其中第k大的节点。

**示例 1:**

```
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
```

**示例 2:**

```
输入: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
输出: 4
```

**限制：**

1 ≤ k ≤ 二叉搜索树元素个数

## 题解

### 题解一：递归方法（二叉树的中序遍历变型（右根左遍历））

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
    public int kthLargest(TreeNode root, int k) {
        List<Integer> list = new ArrayList<>();
        inOrder(root, list);
        return list.get(k - 1);
    }

    private void inOrder(TreeNode node, List<Integer> list) {
        if (node == null) {
            return;
        }
        inOrder(node.right, list);
        list.add(node.val);
        inOrder(node.left, list);
    }
}
```

#### 复杂度分析：

- 时间复杂度：O(n)。
- 空间复杂度：O(n)。

### 解法二：迭代方法（Stack 数据结构）

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
    public int kthLargest(TreeNode root, int k) {
        int count = 1;
        Stack<TreeNode> stack = new Stack<>();
        while (root != null || !stack.empty()) {
            while (root != null) {
                stack.push(root);
                root = root.right;
            }
            TreeNode pop = stack.pop();
            if (count == k) {
                return pop.val;
            }
            count++;
            root = pop.left;
        }
        return 0;
    }
}
```

#### 复杂度分析：

- 时间复杂度：O(n)。
- 空间复杂度：O(n)。
