# LeetCode -- 704. Binary Search (Easy)

    - going to implement the binary search both iteratively and recursively
    - array is pre sorted ascending
    - the target number might not exists
    - return -1 if it does not exist


# Iterative Solution - (Time: O(log(n)), Space: O(n))

    - while loop finding the mid point and comparing against the target until we find or have nothing left

    public int Search(int[] nums, int target) {
        int left = 0;
        int right = nums.Length - 1;
        while (left <= right)
        {
            int mid = (right + left) / 2;

            if (nums[mid] > target)
            {
                right = mid - 1;
            }
            else if (nums[mid] < target)
            {
                left = mid + 1;
            }
            else
            {
                return mid;
            }
        }

        return -1;
    }

# Recursive Solution - (Time: O(log(n)), Space: O(n))

    - 

    public class Solution {
        public int Search(int[] nums, int target) {
            return SearchHelper(nums, target, 0, nums.Length - 1);
        }

        public int SearchHelper(int[] nums, int target, int left, int right)
        {
            if (left > right) { return -1; }
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) { return mid; }
            else if (nums[mid] > target)
            {
                return SearchHelper(nums, target, left, mid - 1);
            }
            else
            {
                return SearchHelper(nums, target, mid + 1, right);
            }
        }
    }

