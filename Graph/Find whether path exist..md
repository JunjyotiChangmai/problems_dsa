**Q. Find whether path exist (GFG)**
```bash
https://www.geeksforgeeks.org/problems/find-whether-path-exist5238/1
```

**Code:**
```bash


class Solution
{
    public:
    //Function to find whether a path exists from the source to destination.
    bool is_Possible(vector<vector<int>>& grid) 
    {
        int n = grid.size();
        
        vector<vector<int>> vis(n, vector<int>(n, 0));
        queue<pair<int, int>> q;
        
        bool ok = false;
        
        for(int i=0; i<n; i++) {
            if(ok) break;
            for(int j=0; j<n; j++) {
                if(grid[i][j] == 1) {
                    q.push({i, j});
                    vis[i][j] = 1;
                    ok = true;
                    break;
                }
            }
        }
        
        int drow[4] = {-1, 0, 1, 0};
        int dcol[4] = {0, -1, 0, 1};
        
        while(!q.empty()) {
            int row = q.front().first;
            int col = q.front().second;
            
            if(grid[row][col] == 2) return true;
            
            q.pop();
            
            for(int i=0; i<4; i++) {
                int nrow = row + drow[i];
                int ncol = col + dcol[i];
                
                if(nrow>=0 && nrow<n && ncol>=0 && ncol<n && !vis[nrow][ncol] && (grid[nrow][ncol] == 3 || grid[nrow][ncol] == 2)) {
                    q.push({nrow, ncol});
                    vis[nrow][ncol] = 1;
                }
            }
        }
        
        return false;
    }
};
```
