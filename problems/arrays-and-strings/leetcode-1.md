# LeetCode -- 1. Two Sum (Easy)

    - input is an integer array and a target integer
    - we are returning an integer array...which contains 2 indices
    - these indices values in the array nums should add up to the target
    - we can assume 1 solution...and can't use the same indice twice
    - order of answer does not matter

    - so we could use a two pointer nested for loop type of solution
    - we could sort first
    - oh jk because the values can be zero...sorting wont help us here actually
    - so lets just implement the solution using two pointer



# Primitive Solution - (Time: O(n), Space: O(n))

    - this is the first quick solution I came up with

    public int[] TwoSum(int[] nums, int target) {
        int i1 = 0;
        int i2 = 0;
        for (int i = 0; i < nums.Length; i++)
        {
            for (int j = i + 1; j < nums.Length; j++)
            {
                if (nums[i] + nums[j] == target)
                {
                    i1 = i;
                    i2 = j;
                    break;
                }
            }
        }

        return new int[] {i1, i2};
    }













