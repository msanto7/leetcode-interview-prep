# LeetCode -- 1732. Find the Highest Altitude (Easy)

    - alright so we are given an int array of net altitude gains
    - so array[i] is the altitude difference between point i and i + 1
    - altitude starts at 0
    
    - so the algorithm seems very simple here...this array basically already is a prefix sum array
    - we just iterate through it once and update a max value from what I can tell



# Optimized Solution - (Time: O(n), Space: O(1))

    - yea so this solution beat 100% of the answers...this took no time at all to do
    - feel like this was too easy honestly....

    public int LargestAltitude(int[] gain) {
        int highest = 0;
        int currHeight = 0;

        for (int i = 0; i < gain.Length; i++)
        {
            currHeight+= gain[i];
            if (currHeight > highest) { highest = currHeight; }
        }

        return highest;       
    }

    