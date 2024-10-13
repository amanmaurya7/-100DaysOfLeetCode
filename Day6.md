# Finding the Longest Common Prefix in an Array of Strings Using Sorting

## Intuition
The idea behind finding the **Longest Common Prefix (LCP)** is to identify characters that are common across all strings in the array. By sorting the array of strings, the strings that share common prefixes are brought closer together, making it easier to compare.

The longest common prefix between the first and last string in the sorted array will be the LCP for the entire array.

## Approach

1. **Sort the Array**:  
   Sorting the array of strings helps bring strings with common prefixes next to each other.

2. **Compare First and Last String**:  
   The longest common prefix between the first and last string in the sorted array will be the longest common prefix for the entire array.

3. **Character Comparison**:  
   Compare characters between the first and last string and incrementally check for matches until a mismatch is found.

4. **Return the Result**:  
   Return the substring from the beginning to the point where characters differ.

## Complexity

- **Time complexity**:  
  - **O(n log n)** due to sorting the array, where **n** is the number of strings.
  - **O(m)** where **m** is the length of the shortest string, for comparing characters between the first and last string.

- **Space complexity**:  
  **O(1)** since no extra space is required apart from the input array and result string.

## Code

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return "";
        
        Arrays.sort(strs);
        String s1 = strs[0];
        String s2 = strs[strs.length - 1];
        int i = 0;
        
        while (i < s1.length() && i < s2.length()) {
            if (s1.charAt(i) == s2.charAt(i)) {
                i++;
            } else {
                break;
            }
        }
        
        return s1.substring(0, i);
    }
}
