
# LeetCode -- 11. Container With Most Water (Medium)

    - alright so again we are show this is a two pointer problem
    - we can start iterating through the array and keeping a running calculation of area
    - we can update a maxArea variable 
    - we don't need to indicate which endpoints or height creates the area but that could be an extension question

    - one of the odd things here is that i am not sure how exactly to move the pointers around to test all options
    - so i created a solution that completely iterates through the array with both pointers...but it times out
    - didn't take long to find which is good...but need to optimize here

    - so the optimized solution is to start with the widest with...and then work your way inward based on the line height
    - the shortest height is the most relevant...so we increment that one and continue to update the max


# Primitive Solution - (Time: O(n^2), Space: O(1))

    public int MaxArea(int[] height) {

        int left = 0, right = 1, maxArea = 0, currArea = 0;

        while (left < height.Length && right < height.Length)
        {
            currArea = Math.Min(height[left], height[right]) * (right - left);

            if (currArea > maxArea)
            {
                maxArea = currArea;
            }

            if (right == height.Length - 1 && left < height.Length - 1)
            {
                left++;
                right = left + 1;
            }
            else //if (right == height.Length - 1 && left == height.Length - 1)
            {
                right++;
            }
        }

        return maxArea;      
    }


# Optimized Solution - (Time: O(n), Space: O(1))

    public int MaxArea(int[] height) {

        int left = 0, right = height.Length - 1, maxArea = 0, currArea = 0;

        while (left < right)
        {
            currArea = Math.Min(height[left], height[right]) * (right - left);

            if (currArea > maxArea)
            {
                maxArea = currArea;
            }

            if (height[left] > height[right])
            {
                right--;
            }
            else
            {
                left++;
            }
        }

        return maxArea;      
    }












