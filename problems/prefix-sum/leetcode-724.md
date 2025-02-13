# LeetCode -- 724. Find Pivot Index (Easy)

    - calculating pivot index from int array
    - pivot index is (sum of all numbers to the left of the index) = (sum of all numbers to right of index)
    - is there gauranteed to be a solution??
    - edges = 0
    - so if no solution exists return -1
    - we are looking for the left most pivot index...so there could be more than 1

    - alright so this is a prefix sum problem...so we could loop through and calc all the sums
    - if i do this once left to right...and once right to left...if there exists a common number between these...then that is what we want



# Primitive Solution - (Time: O(n), Space: O(n))

    - so the first solution wasn't too hard to get too...2 prefix sum arrays then comparing values

    public int PivotIndex(int[] nums) {
        // [0, 1, 8, 11, 17, ]
        // [0, 20, 17, 11, 6, 0]

        int pivotIndex = -1;

        // create 2 prefix sum arrays
        int[] sumLeft = new int[nums.Length];
        sumLeft[0] = 0;
        for (int i = 1; i < nums.Length; i++)
        {
            sumLeft[i] = sumLeft[i - 1] + nums[i - 1];
        }

        int[] sumRight = new int[nums.Length];
        sumRight[nums.Length - 1] = 0;
        for (int i = nums.Length - 2; i >= 0; i--)
        {
            sumRight[i] = sumRight[i + 1] + nums[i + 1];
        }

        for (int i = 0; i < nums.Length; i++)
        {
            if (sumLeft[i] == sumRight[i])
            {
                return i;
            }
        }
        
        return pivotIndex;
    }

# Optimized Solution - (Time: O(n), Space: O(1))

    - the optimized solution avoids using the extra arrays
    - uses the total sum of the input array
    - subtracts the leftSum and the current element to find the rightSum and compares these values on the fly



    public int PivotIndex(int[] nums) {
        int sum = 0;
        int leftSum = 0;

        foreach (var x in nums) { sum += x; }

        for (int i = 0; i < nums.Length; i++)
        {
            if (leftSum == sum - leftSum - nums[i])
            {
                return i;
            }
            
            leftSum += nums[i];
        }

        return -1;
    }
