**Q. All Paths From Source to Target (Leetcode)**
```bash
https://leetcode.com/problems/all-paths-from-source-to-target/
```

**Code:**
```bash
class Solution {
private:
  void dfs(int node, vector<vector<int>> &graph, vector<int> &path, vector<vector<int>> &ans, vector<int> &vis, vector<int> &pathVis, int n) {
    path.push_back(node);
    vis[node] = 1;
    pathVis[node] = 1;

    if(node == n) ans.push_back(path);

    for(auto it : graph[node]) {
        if(!vis[it]) dfs(it, graph, path, ans, vis, pathVis, n);
        else if(!pathVis[it]) dfs(it, graph, path, ans, vis, pathVis, n);
    }

    path.pop_back();
    pathVis[node] = 0;
  }
public:
    vector<vector<int>> allPathsSourceTarget(vector<vector<int>>& graph) {
        int n = graph.size();
        vector<vector<int>> ans;
        vector<int> path;
        vector<int> vis(n, 0);
        vector<int> pathVis(n, 0);
        
        dfs(0, graph, path, ans, vis, pathVis, n-1);

        return ans;
    }
};
```