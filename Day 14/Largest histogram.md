```c++
#include<bits/stdc++.h>
using namespace std;
int largestRectangle(vector < int > & heights) {
   int n = heights.size();
        stack<int>s;
        int leftsmall[n], rightsmall[n];
        for(int i =0;i<n;i++){
            // for find the leftsmaller array
            while(!s.empty() && heights[s.top()] >= heights[i]){
                s.pop();
            }
            if(s.empty())
                leftsmall[i] = 0;
            else
                leftsmall[i] = s.top()+1;
            s.push(i);
        }
        int maxA = 0;
        // for rightsmaller array
        while(!s.empty()) // clear the stack to reused 
            s.pop();
        for(int i =n-1;i>=0;i--){
            while(!s.empty() && heights[s.top()] >= heights[i]){
                s.pop();
            }
            if(s.empty())
                rightsmall[i] = n-1;
            else
                rightsmall[i] = s.top()-1;
            maxA = max(maxA,heights[i]*(rightsmall[i] - leftsmall[i] +1));
            s.push(i);
        }
        return maxA;
 }
 ```
