**Pattern: Hash Set**

**Intuition**
To avoid repeatedly recounting the same sequences, we only want to start counting when we find the beginning of a consecutive sequence.
A number is the start of a sequence if num - 1 is not in the set.
This guarantees that each consecutive sequence is counted exactly once.

Once we identify such a starting number, we simply keep checking if num + 1, num + 2, … exist in the set and extend the streak as far as possible.
This makes the solution efficient and clean because each number contributes to the sequence only one time.

**Algorithm**
Convert the list into a set numSet for O(1) lookups.
Initialize longest to track the length of the longest consecutive sequence.
For each number num in numSet:
Check if num - 1 is not in the set:
If true, num is the start of a sequence.
Initialize length = 1.
While num + length exists in the set, increase length.
Update longest with the maximum length found.
Return longest after scanning all numbers.

class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet <Integer> set = new HashSet<>();
        int longest = 0;
        for(int i = 0; i < nums.length;i++){
            set.add(nums[i]);
        }
        for(int num : set){
            if (!set.contains(num-1)){
                int length = 1;
                while(set.contains(num+length)){
                    length++;
                }
                longest = Math.max(longest, length);
            }
        }
        return longest;
    }
}
