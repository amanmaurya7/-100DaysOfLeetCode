# Sorting Colors – Dutch National Flag Algorithm

## Intuition
The problem requires sorting an array of integers where the values are only `0`, `1`, and `2`. My first thought was to use a counting sort, but a more efficient approach is to use the **Dutch National Flag Algorithm**. This algorithm sorts the array in one pass using a three-pointer technique, making it both time-efficient and space-efficient.

## Approach

1. **Three Pointers**:  
   - **start**: Tracks the position where `0` should go.
   - **mid**: Scans the array to check the current value.
   - **end**: Tracks where `2` should go.

2. **Traverse the Array**:  
   As we traverse the array, we check the value of `nums[mid]`:
   - If `nums[mid] == 0`, swap `nums[start]` and `nums[mid]`, then increment both `start` and `mid`.
   - If `nums[mid] == 1`, simply move `mid` forward.
   - If `nums[mid] == 2`, swap `nums[mid]` and `nums[end]`, and decrement `end`.

3. This process continues until `mid` crosses `end`, ensuring all `0`s are placed at the beginning, all `2`s at the end, and `1`s in between.

## Complexity

- **Time complexity**:  
  **O(n)** as the array is traversed only once.

- **Space complexity**:  
  **O(1)** as the sorting is done in place using constant extra space.

## Code

```java
class Solution {
    public void sortColors(int[] nums) {
        int start = 0, mid = 0;
        int end = nums.length - 1;

        while (mid <= end) {
            if (nums[mid] == 0) {
                swap(nums, start, mid);
                start++;
                mid++;
            } else if (nums[mid] == 1) {
                mid++;
            } else {
                swap(nums, mid, end);
                end--;
            }
        }
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
