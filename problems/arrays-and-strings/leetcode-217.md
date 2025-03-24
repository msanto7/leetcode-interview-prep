# LeetCode -- 217. Contains Duplicate (Easy)

    - inputs is an integer array
    - return true if any value appears atleast twice -- false if they are distinct
    
    - so we definitely need to iterate through the whole array once (assuming no duplicates)
    - otherwise we could exit at first duplicate and return false;
    - I could use a dictionary of counts 
    - actually in this case hashset is better because we don't need the counts...the presence means it occured once


# Primitive Solution - (Time: O(n), Space: O(n))

    - simple and easy hashSet solution that did not take me long to recognize and get to


    public bool ContainsDuplicate(int[] nums) {
        HashSet<int> h = new HashSet<int>();
        for (int i = 0; i < nums.Length; i++)
        {
            if (h.Contains(nums[i])) { return true; }
            h.Add(nums[i]);
        }
        
        return false;
    }






