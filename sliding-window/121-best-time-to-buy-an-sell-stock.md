**Pattern: Sliding Window**

**Optimal Approach:**

- Left pointer = cheapest buy price seen so far
- Right pointer = current sell price, moves every step
- If prices[r] > prices[l] → calculate profit, update max
- If prices[r] <= prices[l] → move left to right (found cheaper buy point)
- Right always increments, left only moves when a cheaper price is found

**Key distinction from Two Pointers:**
- **Two pointers**: start from opposite ends, move toward each other
- **Sliding window**: both start left, move in same direction

**TC: O(n)**
**SC:O(1)**

class Solution {
    public int maxProfit(int[] prices) {
        int l = 0;
        int r = 1;
        int maxp = 0;

        while(r < prices.length){

            if (prices[l] < prices[r]){
                int profit = prices[r] - prices[l];
                maxp = Math.max(maxp, profit);
            }
            else{
                l = r;
            }
            r++;
        }
        return maxp;
    }
}