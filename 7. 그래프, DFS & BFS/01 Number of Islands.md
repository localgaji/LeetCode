## 200. Number of Islands

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. 
You may assume all four edges of the grid are all surrounded by water.

---

#### 풀이 1. 

1. 

```python
class Solution(object):
    def numIslands(self, grid):
        
        # 땅이 없을 경우 리턴 (예외)
        if not grid: 
            return 0
        
        # dfs 함수 : i,j 위치를 시작으로, 인접한 땅이 더 이상 없을 때까지 동서남북을 탐색하여 0으로 변경함
        def oneland(grid, i, j):
            
            # 더 이상 인접한 땅이 없으면 return
            if (i < 0 or i >= len(grid) or 
                j < 0 or j >= len(grid[0]) or 
                grid[i][j] == "0"):
                return
            
            # 이미 검사한 인접땅은 또 count되면 안되므로 바다("0")로 변경
            grid[i][j] = "0"
            
            # 재귀 구조로 동서남북을 탐색
            oneland(grid, i-1 , j)
            oneland(grid, i+1, j)
            oneland(grid, i, j-1)
            oneland(grid, i, j+1)

        count = 0
        
        # 위치를 하나씩 순회하면서 값이 "1"인 경우 -> dfs 함수 실행 : 해당 섬을 전부 바다("0")로 변경 -> count하기
        for i in range(0,len(grid)):
            for j in range(0,len(grid[0])):
                if grid[i][j] == "1":
                    oneland(grid, i, j)
                    count += 1

        return count
```
