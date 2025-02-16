# LeetCode -- 1657. Determine if Two Strings Are Close (Medium)

    - 2 strings as input params...and returning a boolean here
    - a string is considered "close" if you can swap any 2 existing characters...or transform every occurence of one existing character into another existing character
    - return true if the words are "close"

    - alright so I am assuming frequency counts will help us here again
    - first optimization can be comparing the lengths of the strings and returning false if not the same...

    - now after looking through the examples...it appears to me that we have to have the same frequency count of each letter..and the same letters...to be up for being close
    - and I think that might be it...we can swap individual characters....ohhhh....well the second operation actually discounts me on that...
    - there is some relationship there though
    - so we need all of the same letters...and the same frequency counts...just doesn't matter which letter...but either way I need to fill a hashmap and compare both keys and values
    - 




# Optimized Solution - (Time: O(n), Space: O(n))

    - so this is my first solution
    - too kabout 30 minutes total
    - fill 2 dictionarys - 1 per word...then compare the stats to make sure we have all the same letters...and the same frequency counts in general


    public bool CloseStrings(string word1, string word2) {
        // operations cannot do anything about length...so if not the same return false
        if (word1.Length != word2.Length) { return false; }

        Dictionary<char, int> d1 = new Dictionary<char, int>();
        Dictionary<char, int> d2 = new Dictionary<char, int>();

        for (int i = 0; i < word1.Length; i++)
        {
            if (d1.TryGetValue(word1[i], out int curr1)) { d1[word1[i]]++; }
            else { d1.Add(word1[i], 1); }

            if (d2.TryGetValue(word2[i], out int curr2)) { d2[word2[i]]++; }
            else { d2.Add(word2[i], 1); }
        }

        var values1 = d1.Values.ToList();
        var values2 = d2.Values.ToList();
        values1.Sort();
        values2.Sort();

        if (new HashSet<char>(d1.Keys).SetEquals(new HashSet<char>(d2.Keys)) 
            && 
            values1.SequenceEqual(values2)) { return true; }
        else { return false; }
    }