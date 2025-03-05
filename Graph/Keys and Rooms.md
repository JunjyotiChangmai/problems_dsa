**Q. Keys and Rooms (leetcode)**
```bash
https://leetcode.com/problems/keys-and-rooms/
```

**Code:**
```bash
class Solution {
public:
    bool canVisitAllRooms(vector<vector<int>>& rooms) {
        int n = rooms.size();

        vector<int> vis(n, 0);
        queue<int> q;
        q.push(0);
        vis[0] = 1;

        while(!q.empty()) {
            int node = q.front();
            q.pop();

            for(auto it : rooms[node]) {
                if(!vis[it]) {
                    q.push(it);
                    vis[it] = 1;
                }
            }
        }

        int cnt = count(vis.begin(), vis.end(), 1);
        return cnt == n;
    }
};
```
