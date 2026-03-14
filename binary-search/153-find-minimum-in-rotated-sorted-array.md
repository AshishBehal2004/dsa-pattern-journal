**Pattern Name: Binary Search**
**Optimal Approach:**

**Intuition**
A rotated sorted array has one special property:
one part is always sorted, and the other part contains the rotation (and the minimum element).

We can use binary search to identify which side is sorted:

If the left half is sorted, then the minimum cannot be there, so we search the right half.
If the right half is sorted, then the minimum must be in the left half (or at the midpoint).
This lets us eliminate half of the array each time and quickly narrow down to the smallest value.

**Algorithm**
Initialize left = 0, right = n - 1, and store the first element as the current answer.
While left <= right:
If the current window is already sorted, update the answer with nums[left] and stop.
Compute mid.
Update the answer with nums[mid].
If the left half is sorted:
Move search to the right half.
Otherwise:
Search in the left half.
Return the smallest value found.

**TC: O(log n)**
**SC:O(1)**

class Solution {
    public int findMin(int[] nums) {
       int l = 0;
       int r = nums.length-1;
        int res = nums[0];

        while(l <= r){
            int m = (l+r) / 2;
            res = Math.min(res, nums[m]);


            if ( nums[l] < nums[r]){
                res = Math.min(res, nums[l]);
                break;
            }    

            if (nums[m] >= nums[l]){
                l = m+1;
            }
            else{
                r = m-1;
            }
        } 
        return res;
    }
}


**Initial Approach :**

Sort the given array
store the first element in variable (as it will be the smallest element in the array) 
return the variable **

**TC: O(n log n) due to sorting**
**SC: O(1) **

class Solution {
    public int findMin(int[] nums) {
        Arrays.sort(nums);

        int min = nums[0];
        return min;
    }
}