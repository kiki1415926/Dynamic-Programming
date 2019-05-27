# 4. Unique Paths II

![63. Unique Paths II](.gitbook/assets/image%20%281%29.png)

![](.gitbook/assets/image%20%288%29.png)

```text
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        space = [[None for sublst in lst] for lst in obstacleGrid]
        n = len(obstacleGrid)
        m = len(obstacleGrid[0])
        if obstacleGrid[0][0] == 1:
                return 0
        else:
            space[0][0] = 1
        for k in range(1, m):
            if obstacleGrid[0][k] == 1:
                space[0][k] = 0
            else:
                space[0][k] = space[0][k-1]
        for h in range(1, n):
            if obstacleGrid[h][0] == 1:
                space[h][0] = 0
            else:
                space[h][0] = space[h-1][0]
        for i in range(1, n):
            for j in range(1, m):
                if obstacleGrid[i][j] == 1:
                    space[i][j] = 0
                else:
                    space[i][j] = space[i][j-1] + space[i-1][j]
        print(space)
        return space[-1][-1]
```

![](.gitbook/assets/image%20%287%29.png)

