# LeetCode -- 643. Maximum Average Subarray I (Easy)

    - int array and int as input
    - looking for a *contiguous* sub array...whose length is = k
    - this sub array average value should be the max in the array
    - we are returning the max average number

    - so because we have a requirement of the length of the subarray...this should be a fixed sized sliding window solution
    - where window size = k
    - one of my first questions is do we have to handle the array size ver being less than k (just a simple if statement to fix)
        - constraints show that I do not have to do this
    - as i am working through this I should have noticed right away that we are using integer ands returning a double


# Primitive Solution - (Time: O(n), Space: O(1))

    - so this is the firs sort of 2 pointer solution i used but it isn't optimized and times out on large arrays
    - so without the additional passes for finding the average...this really is a single pass at most problem
    - is there a better way to do the average potentially?
    - i tried using linq to calculate the average of the subarray
    - but still exceeded time limit...I am realizing that the optimization has to be in regard to the sliding window
    - 

    public double FindMaxAverage(int[] nums, int k) {
        int left = 0;
        int right = left + (k - 1);
        double maxAvg = Double.MinValue;
        double avg = 0;

        if (nums.Length == k && k == 1) { return nums[0]; }

        // first trying all windows
        while (right < nums.Length)
        {
            // calculate the average - using linq
            for (int i = left; i < left + k; i++)
            {
                avg = avg + nums[i];
            }

            avg = avg / k;

            // update the max if necessary
            if (avg > maxAvg)
            {
                maxAvg = avg;
            }

            // move window
            left++;
            right++;
            avg = 0;
        }

        return maxAvg;    
    }



# Slightly Optimized Solution - (Time: O(n), Space: O(1))

    - so after cleaning up the avg calculation so you only needed to do the full addition pass through the first time
    - this was able to pass time limits despite seemingly being pretty slow still

    public double FindMaxAverage(int[] nums, int k) {
        int left = 0;
        int right = left + (k - 1);
        double maxAvg = Double.MinValue;
        double avg = 0;

        if (nums.Length == k && k == 1) { return nums[0]; }

        // first trying all windows
        while (right < nums.Length)
        {
            // calculate the average - using linq
            if (left == 0)
            {
                avg = nums.Skip(left).Take(k).Average();
            }
            else
            {
                avg = ((avg * k) - nums[left - 1] + nums[right]) / k;
            }   
            
            // update the max if necessary
            if (avg > maxAvg)
            {
                maxAvg = avg;
            }

            // move window
            left++;
            right++;
        }

        return maxAvg;    
    }







