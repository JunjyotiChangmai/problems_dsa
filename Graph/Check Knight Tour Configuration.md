**Q. Check Knight Tour Configuration (Leetcode)**
```bash
https://leetcode.com/problems/check-knight-tour-configuration/
```

**Code:**
```bash
class Solution {
public:
    bool checkValidGrid(vector<vector<int>>& grid) {
        int n = grid.size();
        
        vector<vector<int>> vis(n, vector<int>(n, 0));
        queue<pair<int, int>> q;
        
        q.push({0, 0});
        vis[0][0] = 1;

        int drow[8] = {-2,-2,-1,1,2,2,1,-1};
	    int dcol[8] = {-1,1,2,2,1,-1,-2,-2};
        int cnt = 1;

        while(!q.empty()) {
            int row = q.front().first;
            int col = q.front().second;

            q.pop();
            
            for(int i=0; i<8; i++) {
                int nrow = row + drow[i];
                int ncol = col + dcol[i];

                if(nrow>=0 && nrow<n && ncol>=0 && ncol<n && !vis[nrow][ncol] && grid[nrow][ncol] == cnt) {
                    q.push({nrow, ncol});
                    vis[nrow][ncol] = 1;
                    cnt++;
                }
            }
        }

        for(int i=0; i<n; i++) {
            for(int j=0; j<n; j++){
                if(!vis[i][j]) return false;
            }
        }

        return true;
    }
};
```