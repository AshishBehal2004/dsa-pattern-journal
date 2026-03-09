**Pattern Name: Two Pointers**

**Wrong Approach:**

Split array in half and compare fixed walls
Only checks one combination, misses the actual answer
Never moves pointers inward to explore other pairs

**Optimal Approach:**

Start l=0, r=end
Calculate area = (r-l) * min(heights[l], heights[r])
Track max area seen
Move the shorter wall inward (it's the bottleneck)
Repeat until l meets r

TC: O(n)
SC: O(1)

class Solution {
    public int maxArea(int[] height) {
        int area = 0;
        int result = 0;
        int l = 0;
        int r = height.length-1;

        while(l < r){

            area = (r-l) * Math.min(height[l], height[r]);
            result = Math.max(result, area);

            if ( height[l] < height[r]){
                l++;
            }
            else{
                r--;
            }
        }
        return result;
    }
}