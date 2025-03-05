**Q. BFS of graph (GFG).**
**Link:**
```bash
https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph
```

**Code:**
```bash
class Solution {
  public:
    // Function to return Breadth First Traversal of given graph.
    vector<int> bfsOfGraph(vector<vector<int>> &adj) {
        int n = adj.size();
        
        vector<int> vis(n, 0);
        queue<int> q;
        
        q.push(0);
        vis[0] = 1;
        
        vector<int> ans;
        
        while(!q.empty()) {
            int node = q.front();
            ans.push_back(node);
            
            q.pop();
            
            for(auto it : adj[node]) {
                if(!vis[it]) {
                    q.push(it);
                    vis[it] = 1;
                }
            }
        }
        
        return ans;
    }
};
```