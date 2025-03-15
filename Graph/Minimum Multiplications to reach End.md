**Q. Minimum Multiplications to reach End (GFG)**
```bash
https://www.geeksforgeeks.org/problems/minimum-multiplications-to-reach-end/1
```

**Code:**
```bash
class Solution {
  public:
    int minimumMultiplications(vector<int>& arr, int start, int end) {
        queue<pair<int, int>> q;
        vector<int> dist(100000, 1e9);
        
        q.push({0, start});
        dist[start] = 0;
        
        while(!q.empty()) {
            int node = q.front().second;
            int dis = q.front().first;
            
            q.pop();
            
            if(node == end) return dis;
            
            for(auto it : arr) {
                int adjNode = (it*node)%100000;
                int adjDis = dis + 1;
                
                if(adjDis< dist[adjNode]) {
                    q.push({adjDis, adjNode});
                    dist[adjNode] = adjDis;
                }
            }
        }
        
        return -1;
    }
};
```
