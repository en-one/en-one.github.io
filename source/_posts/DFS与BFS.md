---
title: DFS与BFS
date: 2020-07-03 17:24:17
tags:
- 数据结构 
- leetcode
---
### BFS 层次遍历
```python
class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        
        levels = []
        if root is None:
            return levels
        
        bfs = collections.deque([root])
        
        while len(bfs) > 0:
            levels.append([])
            
            level_size = len(bfs) //记录当前层
            for _ in range(level_size):
                node = bfs.popleft() //出队列
                levels[-1].append(node.val)
                
                if node.left is not None:
                    bfs.append(node.left)
                if node.right is not None:
                    bfs.append(node.right)
        
        return levels

```
### BFS 深度搜索

```python

```
