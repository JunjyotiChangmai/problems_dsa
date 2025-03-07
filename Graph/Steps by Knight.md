**Q. Steps by Knight (GFG)**
```bash
https://www.geeksforgeeks.org/problems/steps-by-knight5927/1
```

**Code:**
```bash

class Solution 
{
    public:
    //Function to find out minimum steps Knight needs to reach target position.
	int minStepToReachTarget(vector<int>&knight,vector<int>&TargetPos,int N)
	{
	    vector<vector<int>> vis(N+1, vector<int>(N+1, 0));
	    queue<pair<pair<int, int>, int>> q;
	    
	    q.push({{knight[0], knight[1]}, 0});
	    vis[knight[0]][knight[1]] = 1;
	    
	    int drow[8] = {-2,-2,-1,1,2,2,1,-1};
	    int dcol[8] = {-1,1,2,2,1,-1,-2,-2};
	    
	    vector<vector<int>> step(N+1, vector<int>(N+1, 0));
	    
	    while(!q.empty()) {
	        int row = q.front().first.first;
	        int col = q.front().first.second;
	        int step = q.front().second;
	        
	        if(row == TargetPos[0] && col == TargetPos[1]) return step;
	        
	        q.pop();
	        
	        for(int i=0; i<8; i++) {
	            int nrow = row + drow[i];
	            int ncol = col + dcol[i];
	            
	            if(nrow>0 && nrow<=N && ncol>0 && ncol<=N && !vis[nrow][ncol]) {
	                q.push({{nrow, ncol}, step+1});
	                vis[nrow][ncol] = 1;
	            }
	        }
	    }
	    
	    return -1;
	}
};
```