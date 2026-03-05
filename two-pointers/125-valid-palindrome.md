**Pattern Name: Two Pointers**

**Approach**:
convert the string to lowercase and store it new string or existing string
 make L pointer pointing to start element
 make R pointer pointing to last element
 
 start a loop till L pointer is less than R 
	make left variable and store the char at L index,
	make right variable and do the above same process but with R
	
	check if the char at L is alphanumeric (using isLetterOrDgit)
		go to next element by increasing L by 1
		
		do the same if check for R as above
		
		
		then check if left matches right
			increase both the pointers (L and R)
			
		otherwise return false
		
		outside the loop return true as by this time, the left would be no L less than R
		
**TC: O(n)**
**SC: O(1)**

class Solution {
    public boolean isPalindrome(String s) {
        s = s.toLowerCase();
        int l = 0;
        int r = s.length()-1;

        while(l < r){
            char left = s.charAt(l);
            char right = s.charAt(r);
            if (!Character.isLetterOrDigit(left)){
                l++;
                continue;
            }
            if (!Character.isLetterOrDigit(right)){
                r--;
                continue;
            }

            if (left == right){
                l++;
                r--;
            }
            else{
                return false;
            }
        }
        return true;


    }
}