**Q. Minimum Number of Vertices to Reach All Nodes (Leetcode)**
```bash
https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/
```

**Code:**
```bash
class Solution {
public:
    vector<int> findSmallestSetOfVertices(int n, vector<vector<int>>& edges) {
        vector<int> res;
        vector<int> indegree(n, 0);
        for(auto it : edges) {
            indegree[it[1]] = 1;
        }

        for(int i=0; i<n; i++) {
            if(indegree[i] == 0)
                res.push_back(i);
        }

        return res;
    }
};
```