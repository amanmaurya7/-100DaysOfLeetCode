# Container With Most Water – Two-Pointer Approach

## Intuition
When tackling the **Container With Most Water** problem, I realized that the area is determined by two factors:
1. The heights of two vertical lines.
2. The distance between them.

The maximum area is formed by two lines that are farthest apart and as tall as possible. A brute force approach would involve checking all possible pairs of lines, but this would be inefficient. The **two-pointer** technique allows us to efficiently narrow down the optimal solution by comparing the heights and moving the pointers accordingly.

## Approach

1. **Two Pointers**:  
   Start with two pointers—one at the beginning (`left = 0`) and one at the end (`right = n-1`) of the array.

2. **Calculate Area**:  
   The area formed by the lines pointed to by `left` and `right` can be calculated using the formula:
   \[
   \text{area} = \min(\text{height[left]}, \text{height[right]}) \times (\text{right} - \text{left})
   \]
   Update the `maxArea` if the current area is greater than the previous maximum.

3. **Move the Pointer**:  
   Move the pointer corresponding to the shorter line, because the height is the limiting factor in determining the area. This is done to maximize the chances of finding a larger area.

4. **Repeat Until the Pointers Meet**:  
   Continue this process until the two pointers meet in the middle, at which point the maximum area has been found.

## Complexity

- **Time complexity**:  
  The time complexity is **O(n)** since we only traverse the array once with two pointers moving towards each other.

- **Space complexity**:  
  The space complexity is **O(1)** since we only use a constant amount of extra space for storing variables like `left`, `right`, `maxArea`, and `currentArea`.

## Code

```java
public class Solution {
    public int maxArea(int[] height) {
        int left = 0;
        int right = height.length - 1;
        int maxArea = 0;
        
        while (left < right) {
            int currentArea = Math.min(height[left], height[right]) * (right - left);
            maxArea = Math.max(maxArea, currentArea);
            
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }
        
        return maxArea;
    }
}
