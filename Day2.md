# 4Sum Problem Solution

## Intuition
When solving the **4Sum** problem, the goal is to find unique quadruplets that sum to the target value. To avoid a brute force solution (which would be inefficient), I used a sorting technique combined with the two-pointer approach to efficiently search for quadruplets. This is similar to the 3Sum problem but extended for four numbers.

## Approach

1. **Sort the Array**:  
   Sorting helps efficiently apply the two-pointer technique and avoids checking unordered pairs multiple times.
   
2. **Fix Two Numbers**:  
   We iterate through the array twice using two loops, where the first loop fixes the first number and the second loop fixes the second number.
   
3. **Two-pointer Technique**:  
   After fixing two numbers, we use the two-pointer technique to find the other two numbers. The two pointers (`a` and `b`) scan the remaining portion of the array.

4. **Skip Duplicates**:  
   To ensure we only add unique quadruplets, we skip duplicate values for each of the four numbers.

5. **Store Results**:  
   I used a `HashSet` to collect unique quadruplets (to avoid duplicates) and then added them to the final result list.

## Complexity

- **Time complexity**:  
  - Sorting the array takes **O(n log n)**.  
  - For each pair of fixed numbers (i and j), we use the two-pointer technique, which takes **O(n²)**.  
  - Hence, the overall time complexity is **O(n³)**.

- **Space complexity**:  
  - The space complexity is **O(k)**, where k is the number of quadruplets in the result. We also use a `HashSet` to store unique results and a list to store the final result. Thus, the space complexity is dominated by the storage of results.

## Code

```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        ArrayList<List<Integer>> li = new ArrayList<>();
        HashSet<List<Integer>> hs = new HashSet<>();
        Arrays.sort(nums);
        
        for (int i = 0; i < nums.length - 3; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            
            for (int j = i + 1; j < nums.length - 2; j++) {
                if (j > i + 1 && nums[j] == nums[j - 1]) continue;
                
                int a = j + 1;
                int b = nums.length - 1;
                
                while (a < b) {
                    long sum = (long) nums[i] + (long) nums[j] + (long) nums[a] + (long) nums[b];
                    
                    if (sum == target) {
                        ArrayList<Integer> temp = new ArrayList<>();
                        temp.add(nums[i]);
                        temp.add(nums[j]);
                        temp.add(nums[a]);
                        temp.add(nums[b]);
                        hs.add(temp);
                        a++;
                        b--;
                    } else if (sum > target) {
                        b--;
                    } else {
                        a++;
                    }
                }
            }
        }
        
        li.addAll(hs);
        return li;
    }
}
