# Two Sum
167. Two Sum II - Input array is sorted (Easy)

[Leetcode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

Double Pointer JAVA solution:

    public int[] twoSum(int[] numbers, int target) {
        if (numbers == null) return null;
        int i = 0, j = numbers.length - 1;
        while (i < j) {
            int sum = numbers[i] + numbers[j];
            if (sum == target) {
                return new int[]{i + 1, j + 1};
            } else if (sum < target) {
                i++;
            } else {
                j--;
            }
        }
        return null;
    }


# Sum of Square Numbers
633. Sum of Square Numbers (Easy)

[Leetcode](https://leetcode.com/problems/sum-of-square-numbers/description/)

JAVA solution:

    class Solution {
        public boolean judgeSquareSum(int c) {
            long left = 0;
            long right = (long) Math.sqrt(c);
            while (left <= right) {
                long sum = left * left + right * right;
                if (sum == c) {
                    return true;
                } else if (sum > c) {
                    right--;
                } else {
                    left++;
                }
            }
            return false;
        }
    }

# Sum of Square Numbers
345. Reverse Vowels of a String (Easy)

[Leetcode](https://leetcode.com/problems/reverse-vowels-of-a-string/description/)

hashmap JAVA solution:

    private final static HashSet<Character> vowels = new HashSet<>(
            Arrays.asList('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'));

    public String reverseVowels(String s) {
        if (s == null) return null;
        int i = 0, j = s.length() - 1;
        char[] result = new char[s.length()];
        while (i <= j) {
            char ci = s.charAt(i);
            char cj = s.charAt(j);
            if (!vowels.contains(ci)) {
                result[i++] = ci;
            } else if (!vowels.contains(cj)) {
                result[j--] = cj;
            } else {
                result[i++] = cj;
                result[j--] = ci;
            }
        }
        return new String(result);
    }
    
two pointer solution:
    class Solution {
        public String reverseVowels(String s) {
            int n = s.length();
            if (n <= 1) return s;

            char[] arr = s.toCharArray();

            int left = 0, right = n - 1;
            while (left < right) {
                // 相等则交换
                if (isVowel(arr[left]) && isVowel(arr[right])) {
                    char tmp = arr[left];
                    arr[left] = arr[right];
                    arr[right] = tmp;

                    left++;
                    right--;
                }

                // 左指针不是元音，右移一位
                if (!isVowel(arr[left])) left++;
                // 右指针不是元音，左移一位
                if (!isVowel(arr[right])) right--;
            }

            return new String(arr);
        }

        // 这里也可以使用List、Set、String代替快速查找
        public boolean isVowel(char c) {
            return c == 'a' || c == 'A'
                    || c == 'e' || c == 'E'
                    || c == 'i' || c == 'I'
                    || c == 'o' || c == 'O'
                    || c == 'u' || c == 'U';
        }
    }
    
680. Valid Palindrome II (Easy)

[Leetcode](https://leetcode.com/problems/valid-palindrome-ii/description/)

![This is an image](https://assets.leetcode-cn.com/solution-static/680/680_fig1.png)

    public boolean validPalindrome(String s) {
    for (int i = 0, j = s.length() - 1; i < j; i++, j--) {
        if (s.charAt(i) != s.charAt(j)) {
            return isPalindrome(s, i, j - 1) || isPalindrome(s, i + 1, j);
        }
    }
    return true;
    }

    private boolean isPalindrome(String s, int i, int j) {
        while (i < j) {
            if (s.charAt(i++) != s.charAt(j--)) {
                return false;
            }
        }
        return true;
    }

88. Merge Sorted Array (Easy)

[Leetcode](https://leetcode.com/problems/merge-sorted-array/description/)



