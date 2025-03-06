**Q. Number of Closed Islands (Leetcode)**
```bash
https://leetcode.com/problems/number-of-closed-islands
```

**Code:**
```bash
class Solution {
private:
    int drow[4] = {-1, 0, 1, 0};
    int dcol[4] = {0, -1, 0, 1};

    void dfs(int row, int col, vector<vector<int>> &grid, vector<vector<int>> &vis, int n, int m) {
        vis[row][col] = 1;

        for(int i=0; i<4; i++) {
            int nrow = row + drow[i];
            int ncol = col + dcol[i];

            if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && !vis[nrow][ncol] && grid[nrow][ncol]==0) {
                dfs(nrow, ncol, grid, vis, n, m);
            }
        }

        grid[row][col] = 1;
    }
public:
    int closedIsland(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();

        vector<vector<int>> tempGrid = grid;
        vector<vector<int>> vis(n, vector<int>(m, 0));

        for(int i=0; i<m; i++) {
            if(!vis[0][i] && tempGrid[0][i] == 0) dfs(0, i, tempGrid, vis, n, m);
            if(!vis[n-1][i] && tempGrid[n-1][i] == 0) dfs(n-1, i, tempGrid, vis, n, m);
        }
        for(int i=0; i<n; i++) {
            if(!vis[i][0] && tempGrid[i][0] == 0) dfs(i, 0, tempGrid, vis, n, m);
            if(!vis[i][m-1] && tempGrid[i][m-1] == 0) dfs(i, m-1, tempGrid, vis, n, m);
        }

        int cnt = 0;

        for(int i=0; i<n; i++) {
            for(int j=0; j<m; j++) {
                if(!vis[i][j] && tempGrid[i][j] == 0) {
                    cnt++;
                    dfs(i, j, tempGrid, vis, n, m);
                }
            }
        }

        return cnt;
    }
};
```