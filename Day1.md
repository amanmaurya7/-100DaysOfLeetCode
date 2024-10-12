# 3Sum Problem Solution

## Intuition
When tackling the **3Sum** problem, I wanted a smart way to find triplets in an array that add up to zero. Instead of using a slow brute-force method, I thought sorting the array and using a two-pointer technique could save time.

## Approach

1. **Sort the Array**:  
   I started by sorting the array, which helps in efficiently finding triplets.
   
2. **Two Pointers**:  
   For each element, I set up two pointers—one just after the current element (`a`) and one at the end of the array (`b`).

3. **Pointer Adjustment**:  
   I calculated the sum of these three numbers (current element, `a`, `b`) and adjusted the pointers based on whether the sum was too high, too low, or just right (zero).

4. **Unique Triplets**:  
   I used a `HashSet` to collect unique triplets and avoid duplicates.

5. **Result Compilation**:  
   Finally, I compiled the unique triplets into a list to return.

## Complexity

- **Time complexity**:  
  - Sorting the array takes \(O(n \log n)\), and for each element, the two-pointer search takes \(O(n)\). Thus, the overall time complexity is **O(n²)**.
  
- **Space complexity**:  
  - The space complexity is **O(n)** for storing unique triplets in the HashSet.

## Code

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        ArrayList<List<Integer>> li = new ArrayList<>();
        HashSet<List<Integer>> hs = new HashSet<>();
        Arrays.sort(nums);
        
        for (int i = 0; i < nums.length; i++) {
            int a = i + 1;
            int b = nums.length - 1;
            
            while (a < b) {
                if (nums[i] + nums[a] + nums[b] == 0) {
                    ArrayList<Integer> temp = new ArrayList<>();
                    temp.add(nums[i]);
                    temp.add(nums[a]);
                    temp.add(nums[b]);
                    hs.add(temp);
                    b--;
                } else if (nums[i] + nums[a] + nums[b] > 0) {
                    b--;
                } else {
                    a++;
                }
            }
        }
        
        for (List<Integer> l : hs) {
            li.add(l);
        }
        
        return li;
    }
}
