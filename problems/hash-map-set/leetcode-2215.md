# LeetCode -- 2215. Find the Difference of Two Arrays (Easy)

    - returning a list of 2 lists
    - 1 contians list of all integer in num1 that are not in num2
    - 2 contains list of all integers in num2 that are not in num1
    - lists must be unique...order does not matter
    - we are using a union intersection type of problem here so hashset might be the way to go

    - I guess just to start as well...the primitive solution of picking an item in list 1...and scanning for it in list 2 and adding if not there...so nested for loops would be the level 0 primitive solution

    - so this feels basic... but I could add all of the elements (or try to) to the hashset...
    - jk i will add 1 array to the hashset...and then check the other array against it filling my list  if the element is not already in the set
    - do this for both arrays and then return the combined built lists


# Primitive Solution - (Time: O(n), Space: O(n))

    - so this first solution took a bit too long...it is relatively simple but also had trouble with the variance issue returning IList<IList<int>
    - I am also relying on linq.Distinct here

    public IList<IList<int>> FindDifference(int[] nums1, int[] nums2) {
        HashSet<int> s = new HashSet<int>();
        IList<IList<int>> response = new List<IList<int>>();
        List<int> first = new List<int>();
        List<int> second = new List<int>();

        // fill the hashset with nums 2
        for (int i = 0; i < nums2.Length; i++)
        {
            s.Add(nums2[i]);
        }

        // create list 1
        for (int i = 0; i < nums1.Length; i++)
        {
            if (!s.Contains(nums1[i]))
            {
                first.Add(nums1[i]);
            }
        }

        s.Clear();

        // fill the hashset with nums 1
        for (int i = 0; i < nums1.Length; i++)
        {
            s.Add(nums1[i]);
        }

        // create list 1
        for (int i = 0; i < nums2.Length; i++)
        {
            if (!s.Contains(nums2[i]))
            {
                second.Add(nums2[i]);
            }
        }

        response.Add(first.Distinct().ToArray());
        response.Add(second.Distinct().ToArray());
        return response;
    }