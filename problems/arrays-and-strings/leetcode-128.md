# LeetCode -- 128. Longest Consecutive Sequence (Medium)

    - unsorted array of integers is the input
    - need to write an algorithm in O(n) time
    - return an integer length of the longest consecutive elements sequence

    - so i feel like the obvious answer is sort...then iterate through and count while updating max
    - going to run with this for now
    - but handling the sort might be an issue if i use a built in...likely people would want the sort implemented
    - 


# Primitive Solution - (Time: O(n), Space: O(n))

    - so here is my original solution with sorting the array
    - but this keeps us out o O(n) for the most part so going to try another method

    public int LongestConsecutive(int[] nums) {
        if (nums.Length == 0) { return 0; }
        if (nums.Length == 1) { return 1; }

        Array.Sort(nums);
        int currLength = 1;
        int maxLength = 1;
        //int last = nums[0];

        for (int i = 1; i < nums.Length; i++)
        {
            if (nums[i] == nums[i - 1] + 1)
            {
                currLength++;              
            }
            else if (nums[i] != nums[i - 1])
            {
                maxLength = Math.Max(maxLength, currLength);
                currLength = 1;
            }
        }

        return Math.Max(maxLength, currLength);
    }


# Optimized Solution - (Time: O(n), Space: O(n))

    - so there is a method that uses a hashset somehow
    - I guess if we just iterate through and insert each value...
    - then we can iterate through the hashset and 











