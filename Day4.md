# Finding the Missing Number in an Array Using Mathematical Summation

## Intuition
The **Missing Number** problem can be efficiently solved using a mathematical formula. The idea is to calculate the expected sum of the first **n** natural numbers and compare it to the sum of the numbers present in the array. The difference between these two sums will give the missing number.

## Approach

1. **Mathematical Formula**:  
   The sum of the first **n** natural numbers can be calculated using the formula:  
   \[
   \text{sum} = \frac{n(n + 1)}{2}
   \]  
   where **n** is the length of the input array (including the missing number).

2. **Calculate the Array Sum**:  
   Iterate through the array to calculate the sum of the numbers present.

3. **Find the Missing Number**:  
   The missing number can be found by subtracting the sum of the array from the expected sum:
   \[
   \text{missing number} = \text{expected sum} - \text{sum of array}
   \]

## Complexity

- **Time complexity**:  
  **O(n)** for iterating through the array to calculate the sum.

- **Space complexity**:  
  **O(1)** since we only use a few extra variables, regardless of the input size.

## Code

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int sum = n * (n + 1) / 2;
        int totalSum = 0;

        for (int num : nums) {
            totalSum += num;
        }
        
        return sum - totalSum;
    }
}
