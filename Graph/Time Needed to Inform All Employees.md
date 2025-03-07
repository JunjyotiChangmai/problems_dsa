**Q. Time Needed to Inform All Employees (Leetcode)**
```bash
https://leetcode.com/problems/time-needed-to-inform-all-employees/
```

**Code:**
```bash
class Solution {
private:
    int dfs(int node, vector<int> &vis, vector<vector<int>> &adj, vector<int> &informTime) {
        vis[node] = 1;
        int ans = informTime[node];
        int mx = 0;

        for(auto it : adj[node]) {
            if(!vis[it]) {
                mx = max(mx, dfs(it, vis, adj, informTime));
            }
        }

        return ans + mx;
    }
public:
    int numOfMinutes(int n, int headID, vector<int>& manager, vector<int>& informTime) {
        vector<vector<int>> adj(n);
        for(int i=0; i<n; i++) {
            if(manager[i] > -1) {
                adj[manager[i]].push_back(i);
            }
        }

        vector<int> vis(n, 0);
        
        return dfs(headID, vis, adj, informTime);
    }
};
```
