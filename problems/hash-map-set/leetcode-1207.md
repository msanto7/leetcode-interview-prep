# LeetCode -- 1207. Unique Number of Occurrences (Easy)

    - alright so we have 1 array...and we are returning a boolean
    - true if num occurences is unique

    - so my first thought is fill a hashset...and then compare length...
    - if not the same length then we have some duplicate elements...going to try this first

    - oh crap okay I need to slow down and read the problem here...after lookin at the examples...this is not what I am finding
    - i need to return true if the num of occurences of each value in the array is unique
    - meaning if i have 3 values (1, 2, 3) they need to show up in different frequences to return true
    - so I am more thinking hashmap for this...push the value and the frequency...
    - then check that they are different


# Optimized Solution - (Time: O(n), Space: O(n))

    - fill hashmap with frequency counts
    - compare values for distinct counts and return bool...fairly simple solution here

    public bool UniqueOccurrences(int[] arr) {
        Dictionary<int, int> d = new Dictionary<int, int>();

        // loop through the array and add or update occurences
        for (int i = 0; i < arr.Length; i++)
        {
            // check if value is already in the hashmap
            if (d.TryGetValue(arr[i], out int curr))
            {
                d[arr[i]]++;
            }
            else
            {
                d.Add(arr[i], 1);
            }
        }

        // next figure out if the values in the dictionary are unique
        var counts = d.Values.ToList();
        var distinctC = counts.Distinct();

        return (counts.Count() == distinctC.Count() ? true : false);
    }
