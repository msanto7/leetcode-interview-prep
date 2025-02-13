# LeetCode -- 1493. Longest Subarray of 1's After Deleting One Element (Medium)

    - input is just a binary array
    - we are returning an int -- size of longest non-empty subarray containing only 1's
    - if no array exists return 0
    - this is after deleting 1 element though
    - this strikes me as basically being leetcode 1004 but with a fixed k
    - so I could still use the sliding window..just only allowing 1 "flip" essentially



# Primitive Solution - (Time: O(n), Space: O(1))




# Optimized Solution - (Time: O(n), Space: O(1))

    -- so optimized solution uses a sliding window that find the longest contiguous sub array of 1s allowing 1 zero
    -- and then we just use that 1 zero as our delete 1 item

    public int LongestSubarray(int[] nums) {
        int left = 0;
        int right = 0;
        int k = 1;

        while (right < nums.Length)
        {
            if (nums[right++] == 0)
            {
                k--;
            }

            if (k < 0 && nums[left++] == 0)
            {
                k++;
            }
        }

        return right - left - 1;
        
    }