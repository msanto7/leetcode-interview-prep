# LeetCode -- 42. Trapping Rain Water (Hard)

    - input is an integer array of heights
    - elevation map with width of each bar = 1
    - compute how much rain water it can trap
    - we are returning an integer for units of rain water that are trapped

    - once again a two pointer problem
    - seems like it would make sense to do sort of a sliding window where we calculate each section of trapped water until it is closed off...then move to the next section
    
    - so i took a stab at this and got somewhat close, but had trouble dialing in what really constituted our cut off criteria as to when to calculate the area
    - so looking at the editorial
    - we are looking for the max level of water thatt can be trapped
    - which is the minimum of maximum height of bars on both sides minus its own height
    - which i basically had in my area calculation anyway
    - i just don't know when to calculate...and when there is another bar that would indicate a bigger area
    - I was trying to do it based on the right most pointer height being greater than or equal to the left pointer height
    - but that doesn't work
    
    - ah okay so the two pointer solution uses the idea that depending on which side the max bar is...thats how we determine which direction to move??
    - we start the pointers at each end
    - and iterate based on which height is the max...and we are constantly adding the area calc somehow

# Primitive Solution - (Time: O(n), Space: O(n))

    - so here is the 2 pointer solution
    - trying to fully understand it though
    https://neetcode.io/solutions/trapping-rain-water
    - alright so it makes sense actually...we are taking the minimum of the max left and right borders form where our current pointer is
    - and so we are calculating the area at each specific position individually 
    - and we swap back and forth from left and right based on the hhighest hight max being on the opposing side...because that is our relevant border

    public int Trap(int[] height) {
        int l = 0;
        int r = height.Length - 1;
        int totalArea = 0;
        int lMax = 0;
        int rMax = 0;

        while (l < r)
        {
            if (height[l] < height[r])
            {
                lMax = Math.Max(lMax, height[l]);
                totalArea += lMax - height[l];
                l++;
            }
            else
            {
                rMax = Math.Max(rMax, height[r]);
                totalArea += rMax - height[r];
                r--;
            }
        }

        return totalArea;        
    }