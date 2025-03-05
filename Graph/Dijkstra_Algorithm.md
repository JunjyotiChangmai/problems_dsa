**Q. Dijkstra Algorithm (GFG).**
```bash
https://www.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/0
```

**1. Code:** Using Priority Queue.
```bash
// User Function Template
class Solution {
  public:
    // Function to find the shortest distance of all the vertices
    // from the source vertex src.
    vector<int> dijkstra(vector<vector<pair<int, int>>> &adj, int src) {
        int n = adj.size();
        
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
        vector<int> dist(n, INT_MAX);
        
        dist[src] = 0;
        pq.push({0, src});
        
        while(!pq.empty()) {
            int node = pq.top().second;
            int dis = pq.top().first;
            
            pq.pop();
            
            for(auto it : adj[node]) {
                int adjNode = it.first;
                int adjDis = it.second;
                
                if(dis + adjDis < dist[adjNode]) {
                    dist[adjNode] = dis + adjDis;
                    pq.push({dis + adjDis, adjNode});
                }
            }
        }
        
        return dist;
    }
};
```
**2. Code:** Using Set Data Structure.
```bash
// User Function Template
class Solution {
  public:
    // Function to find the shortest distance of all the vertices
    // from the source vertex src.
    vector<int> dijkstra(vector<vector<pair<int, int>>> &adj, int src) {
        int n = adj.size();
        
        set<pair<int, int>> st;
        vector<int> dist(n, INT_MAX);
        
        st.insert({0, src});
        dist[src] = 0;
        
        while(!st.empty()) {
            auto it = *(st.begin());
            int node = it.second;
            int distance = it.first;
            st.erase(it);
            
            for(auto e : adj[node]) {
                int adjNode = e.first;
                int adjDist = e.second;
                
                if(distance + adjDist < dist[adjNode]) {
                    dist[adjNode] = distance + adjDist;
                    st.insert({adjDist + distance, adjNode});
                }
            }
        }
        
        return dist;
    }
};
```
