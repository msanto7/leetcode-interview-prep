# LeetCode -- 1679. Max Number of K-Sum Pairs (Medium)

    - so the idea is that we count the amount of "operations" which is taking 2 numbers and adding to k
    - we are looking for the maximum number of operations to get to the sum of k
    - is the array sorted? are the numbers in the array always less than k?
    - so there is an obvious brute force approach attempting every pair
    - but two pointer can help optimize 
    - constraints say no negative values 
        - not a huge deal but would change some of my logic for optimizing the pointers
    - so my primitve solution sorts the array...and then does a standard 2 pointer moving differently depending on the 
    sum being greater than or less than k



# Primitive Solution - (Time: O(n), Space: O(1)) (sort time as well though)

    public int MaxOperations(int[] nums, int k) {
        int numOps = 0;
        int left = 0, right = nums.Length - 1;
        Array.Sort(nums);

        while (left < right)
        {
            if (nums[right] > k) { right--; }
            else if ((nums[left] + nums[right]) == k)
            {
                numOps++;
                left++;
                right--;
            }
            else if (nums[left] + nums[right] > k)
            {
                right--;
            }
            else
            {
                left++;
            }        
        }
        return numOps;     
    }


# Optimized Solution - (Time: O(n), Space: O(1))







