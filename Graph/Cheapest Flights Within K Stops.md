**Q. Cheapest Flights Within K Stops (Leetcode)**
```bash
https://leetcode.com/problems/cheapest-flights-within-k-stops/description
```

**Code:**
```bash
class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int k) {
        vector<vector<pair<int, int>>> adj(n);
        for(auto it : flights) {
            int u = it[0];
            int v = it[1];
            int w = it[2];

            adj[u].push_back({v, w});
        }

        vector<int> costs(n, 1e9);
        queue<pair<int, pair<int, int>>> q;

        q.push({0, {src, 0}});
        costs[src] = 0;

        while(!q.empty()) {
            int node = q.front().second.first;
            int cost = q.front().second.second;
            int stops = q.front().first;

            q.pop();

            if(stops > k) continue;

            for(auto it : adj[node]) {
                int adjNode = it.first;
                int adjCost = it.second;

                if(cost + adjCost < costs[adjNode] && stops <= k) {
                    q.push({stops + 1, {adjNode, cost + adjCost}});
                    costs[adjNode] = cost + adjCost;
                }
            }  
        }

        if(costs[dst] == 1e9) return -1;
        return costs[dst];

    }
};
```