# [面试题 03.05\. 栈排序](https://leetcode-cn.com/problems/sort-of-stacks-lcci/)

Difficulty: **中等**

栈排序。 编写程序，对栈进行排序使最小元素位于栈顶。最多只能使用一个其他的临时栈存放数据，但不得将元素复制到别的数据结构（如数组）中。该栈支持如下操作：`push`、`pop`、`peek` 和 `isEmpty`。当栈为空时，`peek` 返回 -1。

**示例1:**

```
 输入：
["SortedStack", "push", "push", "peek", "pop", "peek"]
[[], [1], [2], [], [], []]
 输出：
[null,null,null,1,null,2]
```

**示例2:**

```
 输入： 
["SortedStack", "pop", "pop", "push", "pop", "isEmpty"]
[[], [], [], [1], [], []]
 输出：
[null,null,null,null,null,true]
```

**说明:**

1.  栈中的元素数目在[0, 5000]范围内。


## 题解

### 题解一：临时辅助栈

```java
class SortedStack {

    Stack<Integer> minStack = new Stack<Integer>();
    Stack<Integer> tempStack = new Stack<Integer>();

    public SortedStack() {

    }
    
    public void push(int val) {
        while (!minStack.isEmpty() && minStack.peek() < val) {
            tempStack.push(minStack.pop());
        }
        minStack.push(val);
        while (!tempStack.isEmpty()) {
            minStack.push(tempStack.pop());
        }
    }
    
    public void pop() {
        if (minStack.isEmpty()) {
            return;
        }
        minStack.pop();
    }
    
    public int peek() {
        if (minStack.isEmpty()) {
            return -1;
        }
        return minStack.peek();
    }
    
    public boolean isEmpty() {
        return minStack.isEmpty();
    }
}

/**
 * Your SortedStack object will be instantiated and called as such:
 * SortedStack obj = new SortedStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.isEmpty();
 */
```