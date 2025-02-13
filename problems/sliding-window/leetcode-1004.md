
# LeetCode -- 1004. Max Consecutive Ones III (Medium)
    - alright so we are returning a max - number of consecutive 1's in a binary int array
    - but we have the ability to flip 0s...k amount of times
    - so my first question is...does flipping matter? like will flipping take you from the not the longest ...to the longest?
    - and I am assuming you can flip zeros in any place across the sub array
    - also there is no specified length of the sub array...it is based on consecutive 1s...so we are using a variable-length sliding window approach

    - this is also tricky because we have to keep track of the zeros just as much as we do the 1's count because we need to know where they can be flipped
    - so i will only be flipping zeros to connect to other subarrays of 1's
    - 



# Primitive Solution - (Time: O(n), Space: O(1))

    - okay so my first primitive solution wasn't too hard to get too
    - there is definitely an way to make it faster by tracking what is coming in and out of the window 1 at a times

    public int LongestOnes(int[] nums, int k) {
        int left = 0;
        int right = 0;
        int numO = 0;
        int numConsec = 0;
        int numFlipped = 0;
        int max = 0;

        while (right < nums.Length)
        {
            if (nums[right] == 1)
            {
                numConsec++;
                max = (numConsec > max ? numConsec : max);
                right++;
            }
            else if (nums[right] == 0 && numFlipped < k)
            {
                numFlipped++;
                numConsec++;
                max = (numConsec > max ? numConsec : max);
                right++;
            }
            else
            {
                left++;
                right = left;
                max = (numConsec > max ? numConsec : max);
                numFlipped = 0;
                numConsec = 0;
            }      
        }
        return max;
    }


# Optimized Solution - (Time: O(n), Space: O(1))

    -- the more efficient solution does the 1 by one and uses the pointers to track the num of consecutive 1's
    -- we also use k to kee better track of what is going on instead of resetting all these int values
    -- so this way we skip over more situations where we maxed the flips and left pointer doesn't help get us back to k = 0 (meaning max flips took place)


    public int LongestOnes(int[] nums, int k) {
        int left = 0, right = 0;
        while (right < nums.Length) {
            if (nums[right++] == 0) {
                k--;
            }
            if (k < 0) {
                if (nums[left++] == 0) {
                    k++;
                }
            }
        }
        return right - left;
    }
