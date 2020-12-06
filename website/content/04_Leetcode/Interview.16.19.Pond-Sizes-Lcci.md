# [面试题 16.19\. 水域大小](https://leetcode-cn.com/problems/pond-sizes-lcci/)

Difficulty: **中等**

你有一个用于表示一片土地的整数矩阵`land`，该矩阵中每个点的值代表对应地点的海拔高度。若值为0则表示水域。由垂直、水平或对角连接的水域为池塘。池塘的大小是指相连接的水域的个数。编写一个方法来计算矩阵中所有池塘的大小，返回值需要从小到大排序。

**示例：**

```shell
输入：
[
  [0,2,1,0],
  [0,1,0,1],
  [1,1,0,1],
  [0,1,0,1]
]
输出： [1,2,4]
```

**提示：**

*   `0 < len(land) <= 1000`
*   `0 < len(land[i]) <= 1000`

## 题解

## 题解一：DFS（广度优先搜索）

```java
class Solution {
    public int[] pondSizes(int[][] land) {
        List<Integer> list = new ArrayList<>();
        if(land.length == 0) {
            return new int [0];
        }
        int temp = 0;
        for(int i = 0; i < land.length; i++) {
            for(int j = 0; j < land[0].length; j++) {
                if(land[i][j] == 0){
                    temp = dfs(land, i, j);
                    list.add(temp);
                }
            }
        }
        list.sort((o1, o2) -> o1 - o2);
        return list.stream().mapToInt(Integer::intValue).toArray();
    }
    
    private int dfs(int[][] land, int i, int j) {
        if(i < 0 || j < 0 || i >= land.length || j >= land[0].length || land[i][j] != 0) {
            return 0;
        }
        land[i][j] = 3;
        int area = 1;
        area += dfs(land, i - 1, j - 1);
        area += dfs(land, i - 1, j + 1);
        area += dfs(land, i, j + 1);
        area += dfs(land, i, j - 1);
        area += dfs(land, i - 1, j);
        area += dfs(land, i + 1, j);
        area += dfs(land, i + 1, j - 1);
        area += dfs(land, i + 1, j + 1);
        return area;
    }
}
```

**复杂度分析**

- 时间复杂度：

- 空间复杂度：

