**Q. Word Search (GFG)**
```bash
https://www.geeksforgeeks.org/problems/word-search/1
```

**Code:**
```bash
class Solution {
  private:
    void dfs(int row, int col, vector<vector<int>> &vis, vector<vector<char>> &mat, string &word, string &res, int pos) {
        vis[row][col] = 1;
        res[pos] = word[pos];
        
        int n = mat.size();
        int m = mat[0].size();
        
        int drow[4] = {-1, 0, 1, 0};
        int dcol[4] = {0, -1, 0, 1};
        
        for(int i=0; i<4; i++) {
            int nrow = row + drow[i];
            int ncol = col + dcol[i];
                
            if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && !vis[nrow][ncol] && mat[nrow][ncol] == word[pos+1]) {
                dfs(nrow, ncol, vis, mat, word, res, pos+1);
            }
        }
        
        vis[row][col] = 0;
        
    }
  public:
    bool isWordExist(vector<vector<char>>& mat, string& word) {
        int n = mat.size();
        int m = mat[0].size();
        
        string s;
        for(auto it : word) {
            s.push_back('$');
        }
        
        for(int i=0; i<n; i++) {
            for(int j=0; j<m; j++) {
                if(mat[i][j] == word[0]) {
                    string res = s;
                    vector<vector<int>> vis(n, vector<int>(m, 0));
                    
                    dfs(i, j, vis, mat, word, res, 0);
                    
                    if(word == res) return true;
                }
            }
        }
        
        return false;
    }
};
```