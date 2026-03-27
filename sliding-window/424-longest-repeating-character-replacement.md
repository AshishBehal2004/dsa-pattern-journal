Pattern: Sliding Window

**Intuition**
We want the longest window where we can make all characters the same using at most k replacements.
The key insight is that the window is valid as long as:

window size – count of the most frequent character ≤ k

Why?
Because the characters that aren't the most frequent are the ones we would need to replace.

So while expanding the window, we track:

the frequency of each character,
the most frequent character inside the window (maxf).
If the window becomes invalid, we shrink it from the left.
This gives us one clean sliding window pass.

**Algorithm**
Create a frequency map count and initialize l = 0, maxf = 0, and res = 0.
Move the right pointer r across the string:
Update the frequency of s[r].
Update maxf with the highest frequency seen so far.
If the window is invalid (window size - maxf > k):
Shrink the window from the left and adjust counts.
Update the result with the valid window size.
Return res at the end.

**TC: O( n )**
**SC: O( n )**
**Where n is the length of the string and  m is the total number of unique characters in the string.**


class Solution {
    public int characterReplacement(String s, int k) {
        int l = 0;
        int res = 0;
        int maxf = 0;
        HashMap<Character, Integer> map = new HashMap<>();

        for(int r = 0; r < s.length(); r++){
            map.put(s.charAt(r), map.getOrDefault(s.charAt(r), 0) + 1);

            maxf = Math.max(maxf, map.get(s.charAt(r)));

            while((r-l+1) - maxf > k){

                map.put(s.charAt(l), map.getOrDefault(s.charAt(l), 0) - 1);
                l+=1;
            }

            res = Math.max(res, r-l+1);
        }
        return res;
    }
}