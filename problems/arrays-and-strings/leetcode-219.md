# LeetCode -- 219. Contains Duplicate II (Easy)

    - integer array and 1 integer as input
    - return true if there are 2 distinct indices i and j - such that...
    - nums[i] == nums[j] and abs(i - j) <= k

    - so similar concept as regular contains duplicate...just need to use a dictionary instead of a hashset so we can keep track of the index at each value
    - going to build a solution with that in mind

    - so I have a working solution like this but it exceeds time limits (which seems odd)
    - it only exceeds time limits in the submit...not the run
    - but also I am not sure of a great way to optimize this
    - maybe some form of a sliding window for this?
    - although that is kind of what I am doing by removing the element from the dictionary if we find a dupe and it is already out of range
    - 


# Primitive Solution - (Time: O(n), Space: O(n))


    - this solution timed out but I think this is fine
    - 1 more optimization would be to use a sliding window and a hash set



    public bool ContainsNearbyDuplicate(int[] nums, int k) {
        Dictionary<int, int> d = new Dictionary<int, int>();
        for (int i = 0; i < nums.Length; i++)
        {
            if (d.ContainsValue(nums[i]))
            {
                var index1 = i;
                var index2 = d.FirstOrDefault(x => x.Value == nums[i]).Key;
                if (Math.Abs(index1 - index2) <= k) { return true;}
                d.Remove(index2);               
            }
            d.Add(i, nums[i]);
        }

        return false;
    }


# Optimized Solution - (Time: O(n), Space: O(n))

    - this solution did pass...and makes more sense
    - it is using a hashSet...but also a sliding window
    - so it cleans up the duplicate key problem i was having above

    public bool ContainsNearbyDuplicate(int[] nums, int k) {
        HashSet<int> h = new HashSet<int>();
        for (int i = 0; i < nums.Length; i++)
        {
            if (h.Contains(nums[i])) { return true; }

            h.Add(nums[i]);

            if (h.Count > k)
            {
                h.Remove(nums[i - k]);
            }
        }

        return false;
    }




    