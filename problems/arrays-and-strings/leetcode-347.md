# LeetCode -- 347. Top K Frequent Elements (Medium)

    - input is an integer array and an integer
    - we are returning an integer array
    - so we are returning the k most frequent elements from the input array
    - order of the elements does not matter
    - answer is guaranteed to be unique - so there are no ties
    - there is a follow up that time complexity must be better than O(nlogn)

    - first we can just return the element if it i - ohhh also k must be >= 1
    - so if 1 element in the array just return the array
    - otherwise we need a frequency count
    - but I imagine there is a way to optimize so that if one number is a certain frequency of k that it has to be part of the return array
    - I suppose that would be more than half?? - or atleast half of k?
    - also I wonder if ordering is helpful or not
    - I guess it just depends
    - so lets say i don't sort...but I fill a dictionary...and if the count every goes above n/2...then we automatically add that to the array??

    - only problem is that i still have to traverse the whole array?
    - i guess not though...i just continue checking if the return array is length k and break if so
    - alright i am going to try to implement with this in mind

    - 



    

# Primitive Solution - (Time: O(nlogn), Space: O(n))

    - so this is my initial solution - took me 20 minutes to come up with

    public int[] TopKFrequent(int[] nums, int k) {
        if (nums.Length == 1) { return nums; }

        Dictionary<int, int> d = new Dictionary<int, int>();
        int[] response = new int[k];
        int j = 0;

        for (int i = 0; i < nums.Length; i++)
        {
            if (!d.ContainsKey(nums[i])) { d.Add(nums[i], 1); }
            else { d[nums[i]]++; }
        }

        // fill in any that remain
        while (j <= k - 1)
        {
            var next = d.OrderByDescending(k => k.Value).FirstOrDefault();
            response[j] = next.Key;
            d.Remove(next.Key);
            j++;
        }

        return response;
    }

# Optimized Solution - (Time: O(nlogn), Space: O(n))

    - so there are some similar solutions that use a heap a well
    - not sure why though at the moment
    - there is also a quick select but this is a pretty cumbersome solution - will come back and look at the optimized















