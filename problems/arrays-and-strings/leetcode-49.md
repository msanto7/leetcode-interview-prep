# LeetCode -- 49. Group Anagrams (Medium)

    - we are given an arrary of strings
    - we need to group the anagrams together
    - an anagram will contain all of the same letters the same amount of times just rearranged
    - so we are recognizing all the words that are anagrams...and return a list of lists
    - so we almost need to iterate through each string...create a dictionary for that string so letters and counts
    - and then check for anagrams and add to a new list
    - we can always eliminate the ones that are used though

    - i feel like because we are only using lowercase letters...we actually might be better off here ordering and using the ascii compare?

    - jk so I am trying to implement the solution where I add a dictionary to a list for each word in the array
    - I have that part done...
    - now I need to address how to loop back through the dictionaries and compare them to each other
    - so I need to make sure that if after ordering them...the dictionaries are equal...then I need to add the string at that index from the input into a list of strings
    
    - I have 2 issues with my current solution
    - I am not removing the indice technically when iterating through and finding a match
    - and I am not adding the individual strings that have no match

    - looked through the editorial after a while because my solution was not taking advantage of some of the properties of anagrams
    - rewrote it using the idea that a sorted string and its sorted anagram are equal


# Primitive Solution - (Time: O(n), Space: O(n))

    - based on sorted strings
    
    public IList<IList<string>> GroupAnagrams(string[] strs) {

        var d = new Dictionary<string, List<string>>();
        foreach (var s in strs)
        {
            var c = s.ToCharArray();
            Array.Sort(c);
            var key = new String(c);

            if (!d.ContainsKey(key))
            {
                d[key] = new List<string>();
            }
            d[key].Add(s);
        }

        return new List<IList<string>>(d.Values);
    }   















