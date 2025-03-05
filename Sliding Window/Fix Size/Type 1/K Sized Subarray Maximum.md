**Q. K Sized Subarray Maximum (GFG).**
```bash
https://www.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101/1
```

**Code:**
```bash

class Solution {
  private: 
    int maxElementQueue(queue<int> q) {
        if(q.empty()) return -1;
        int mx = INT_MIN;
        
        while(!q.empty()) {
            int val = q.front();
            q.pop();
            
            mx = max(mx, val);
        }
        
        return mx;
    }
  public:
    vector<int> maxOfSubarrays(vector<int>& arr, int k) {
        int n = arr.size();
        int r=0;
        
        queue<int> q;
        
        while(r<k) {
            q.push(arr[r]);
            r++;
        }
        
        int mx = maxElementQueue(q);
        vector<int> ans;
        ans.push_back(mx);
        
        int pre_max = mx;
        
        while(r<n) {
            int front_val = q.front();
            q.pop();
            
            q.push(arr[r]);
            
            if(front_val == pre_max) mx = maxElementQueue(q);
            else mx = max(pre_max, arr[r]);
            
            ans.push_back(mx);
            pre_max = mx;
            r++;
        }
        
        return ans;
    }
};
```
