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

