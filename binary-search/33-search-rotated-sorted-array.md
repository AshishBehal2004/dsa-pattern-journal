**Optimal Approach:**

- Use standard binary search with l, r, m
- At each step, one half is always sorted — figure out which one by comparing nums[l] and nums[m]
- If nums[l] <= nums[m] → left half is sorted, otherwise right half is sorted
- Once we know which half is sorted, check if target falls outside that half's range
- If outside → target can't be there, eliminate it, search the other half
- If inside → search that half
- Keep halving until target is found or return -1

**TC: O(log n)**
**SC: O(1)**

class Solution {
    public int search(int[] nums, int target) {
        int l = 0;
        int r = nums.length - 1;
        
        while(l <= r){

            int m = (l + r) / 2;

            if (target == nums[m]){
                return m;
            }

            if (nums[l] <= nums[m]){
                if (target < nums[l] || target > nums[m]){
                    l = m + 1;
                }
                else{
                    r = m - 1;
                }
            }
            else{
                if(target < nums[m] || target > nums[r]){
                    r = m - 1;
                }
                else{
                    l = m + 1;
                }
            }
        }
        return -1;
    }
}

**Linear Approach:**
- Loop through every element one by one
- check if the element matches the target
- repeat n times until u reach the end.

**TC: O(n)**
**SC: O(1)**

class Solution {
    public int search(int[] nums, int target) {
        for(int i = 0; i < nums.length;i++){
            if (nums[i] == target){
                return i;
            }
        }
        return -1;
    }
}
