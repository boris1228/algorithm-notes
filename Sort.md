# Kth Element
215. Kth Largest Element in an Array (Medium)

[Leetcode](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

Brutal force:

    import java.util.Arrays;

    public class Solution {

        public int findKthLargest(int[] nums, int k) {
            int len = nums.length;
            Arrays.sort(nums);
            return nums[len - k];
        }
    }
    

