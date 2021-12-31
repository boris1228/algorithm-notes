# BinarySearch
69. Sqrt(x) (Easy)

[Leetcode](https://leetcode.com/problems/sqrtx/description/)

Binary Search

        class Solution {
            public int mySqrt(int x) {
                int l = 0, r = x, ans = -1;
                while (l <= r) {
                    int mid = l + (r - l) / 2;
                    if ((long) mid * mid <= x) {
                        ans = mid;
                        l = mid + 1;
                    } else {
                        r = mid - 1;
                    }
                }
                return ans;
            }
        }

744. Find Smallest Letter Greater Than Target (Easy)

[Leetcode](https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/)


        public char nextGreatestLetter(char[] letters, char target) {
            int n = letters.length;
            int l = 0, h = n - 1;
            while (l <= h) {
                int m = l + (h - l) / 2;
                if (letters[m] <= target) {
                    l = m + 1;
                } else {
                    h = m - 1;
                }
            }
            return l < n ? letters[l] : letters[0];
        }
       
       
 540. Single Element in a Sorted Array (Medium)

[Leetcode](https://leetcode-cn.com/problems/single-element-in-a-sorted-array/description/)

        class Solution {
            public int singleNonDuplicate(int[] nums) {
                int lo = 0;
                int hi = nums.length - 1;
                while (lo < hi) {
                    int mid = lo + (hi - lo) / 2;
                    boolean halvesAreEven = (hi - mid) % 2 == 0;
                    if (nums[mid + 1] == nums[mid]) {
                        if (halvesAreEven) {
                            lo = mid + 2;
                        } else {
                            hi = mid - 1;
                        }
                    } else if (nums[mid - 1] == nums[mid]) {
                        if (halvesAreEven) {
                            hi = mid - 2;
                        } else {
                            lo = mid + 1;
                        }
                    } else {
                        return nums[mid];
                    }
                }
                return nums[lo];
            }
        }


