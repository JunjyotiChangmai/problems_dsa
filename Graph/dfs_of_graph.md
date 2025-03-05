**Q. DFS of Graph (GFG).**
```bash
https://www.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/0
```

**Code:**
```bash
class Solution {
  private:
    void dfs(int node,vector<int> &vis, vector<vector<int>> &adj, vector<int> &ans) {
        vis[node] = 1;
        ans.push_back(node);
        for(auto it : adj[node]){
            if(!vis[it]) {
                dfs(it, vis, adj, ans);
            }
        }
    }
  public:
    // Function to return a list containing the DFS traversal of the graph.
    vector<int> dfsOfGraph(vector<vector<int>>& adj) {
        // Code here
        int n = adj.size();
        
        vector<int> ans;
        vector<int> vis(n, 0);
        
        dfs(0, vis, adj, ans);
        
        return ans;
    }
};
```
