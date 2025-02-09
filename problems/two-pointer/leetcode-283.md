
# LeetCode -- 283. Move Zeroes (Easy)
    - so this is grouped as a 2 pointer solution
    - my first thought is to iterate through and move the nonzero nums to the front
    - while keeping a count...and just setting the rest as zeroes
    - going to try to implement that first...seems like a decently optimized solution



# Primitive Solution - (Time: O(n), Space: O(n))

    - first solution I came up with...

    public void MoveZeroes(int[] nums) {
        int left = 0;
        int right = 0;
        int count0 = 0;

        if (nums.Length > 1)
        {
            while (left < nums.Length && right < nums.Length)
            {
                if (nums[right] != 0)
                {
                    nums[left] = nums[right];
                    if (right != left) { nums[right] = 0; }
                    left++;
                    right++;
                }
                else
                {
                    right++;
                }
            }
        }    
    }





# Optimized Solution - (Time: O(n), Space: O(1))






