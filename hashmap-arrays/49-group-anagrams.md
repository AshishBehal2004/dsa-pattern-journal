**Pattern Name:HashMap + Character Frequency as Key**

**Intuition**
Instead of sorting each string, we can represent every string by the frequency of its characters.
Since the problem uses lowercase English letters, a fixed-size array of length 26 can capture how many times each character appears.
Two strings are anagrams if and only if their frequency arrays are identical.
By using this frequency array (converted to a tuple so it can be a dictionary key), we can group all strings that share the same character counts.

**Algorithm**
Create a hash map where each key is a 26-length tuple representing character frequencies, and each value is a list of strings belonging to that anagram group.
For each string in the input:
Initialize a count array of size 26 with all zeros.
For each character c in the string, increment the count at the corresponding index.
Convert the count array to a tuple and use it as the key.
Append the string to the list associated with this key.
After processing all strings, return all the lists stored in the hash map

Time complexity: O(m x n)because for every word (m words), we loop through each character (n = average length) to build the count array.

Space COmplexity: O(m × n) because we store every word in the hashmap, and in the worst case all m words of length n are stored across the lists.

public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> map = new HashMap<>();
        
        List<List<String>> result = new ArrayList<>();
        for(String s : strs){
            int[] count = new int[26];
            for(char c : s.toCharArray()){
                count[c - 'a'] += 1;
            }
            String key = Arrays.toString(count);
            map.putIfAbsent(key, new ArrayList<>());
            map.get(key).add(s);
        }

        for(Map.Entry<String, List<String>> entry : map.entrySet()){
            result.add(entry.getValue());
        }
        return result;

        