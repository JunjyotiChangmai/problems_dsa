**Q. Number of Ways to Arrive at Destination (Leetcode)**
```bash
https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/description/
```

**Code:**
```bash
class Solution {
public:
    int countPaths(int n, vector<vector<int>>& roads) {
        vector<vector<pair<int, int>>> adj(n);
        for(auto it : roads) {
            int u = it[0];
            int v = it[1];
            int w = it[2];

            adj[u].push_back({v, w});
            adj[v].push_back({u, w});
        }

        priority_queue<pair<long long, int>, vector<pair<long long, int>>, greater<pair<long long, int>>> pq;
        vector<long long> dist(n, 1e18);
        vector<int> ways(n, 0);

        pq.push({0, 0});
        dist[0] = 0;
        ways[0] = 1;

        int mod = (int)(1e9+7);

        while(!pq.empty()) {
            int node = pq.top().second;
            long long dis = pq.top().first;

            pq.pop();

            for(auto it : adj[node]) {
                int adjNode = it.first;
                long long adjDis = it.second;

                if(dis + adjDis < dist[adjNode]) {
                    pq.push({dis + adjDis, adjNode});
                    dist[adjNode] = dis + adjDis;
                    ways[adjNode] = ways[node];
                }
                else if(dis + adjDis == dist[adjNode]) {
                    ways[adjNode] = (ways[adjNode] + ways[node]) % mod;
                }
            }
        }

        return ways[n-1] % mod;
    }
};
```