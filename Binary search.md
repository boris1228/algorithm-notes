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

method 2: only search for even index:

        class Solution {
            public int singleNonDuplicate(int[] nums) {
                int lo = 0;
                int hi = nums.length - 1;
                while (lo < hi) {
                    int mid = lo + (hi - lo) / 2;
                    if (mid % 2 == 1) mid--;
                    if (nums[mid] == nums[mid + 1]) {
                        lo = mid + 2;
                    } else {
                        hi = mid;
                    }
                }
                return nums[lo];
            }
        }
        
278. First Bad Version (Easy)

[Leetcode](https://leetcode-cn.com/problems/first-bad-version/)

        public class Solution extends VersionControl {
            public int firstBadVersion(int n) {
                int left = 1, right = n;
                while (left < right) { // ????????????????????????????????????
                    int mid = left + (right - left) / 2; // ?????????????????????
                    if (isBadVersion(mid)) {
                        right = mid; // ??????????????? [left, mid] ???
                    } else {
                        left = mid + 1; // ??????????????? [mid+1, right] ???
                    }
                }
                // ????????? left == right???????????????????????????????????????
                return left;
            }
        }

153. Find Minimum in Rotated Sorted Array (Medium)

[Leetcode](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/)



                public int findMin(int[] nums) {
                    int l = 0, h = nums.length - 1;
                    while (l < h) {
                        int m = l + (h - l) / 2;
                        if (nums[m] <= nums[h]) {
                            h = m;
                        } else {
                            l = m + 1;
                        }
                    }
                    return nums[l];
                }


34. Find First and Last Position of Element in Sorted Array

[Leetcode](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)


