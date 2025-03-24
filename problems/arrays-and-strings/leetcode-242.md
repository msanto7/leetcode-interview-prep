# LeetCode -- 242. Valid Anagram (Easy)

    - we are given 2 strings as input s and t
    - we need to determine if t is an anagram of s and return true/false
    - so it sounds like the length of the 2 strings has to be the same??
    - based on examples we need all of the original letters to be an anagram
    - I am going to assume also that a string can be an anagram of itself ** - good quesiton to ask interviewers

    - I could fill 2 dictionaries and compare at the end if they are equal
    - I could also maybe do some type of reordering of the characters in an array base on ascii??
    - and then compare item by item


# Primitive Solution - (Time: O(n), Space: O(n))

    - this was the first quick solution I came up with using 2 dictionaries

    public class Solution {
        public bool IsAnagram(string s, string t) {
            var sDictionary = CreateDictionary(s);
            var tDictionary = CreateDictionary(t);

            return sDictionary.OrderBy(k => k.Key).SequenceEqual(tDictionary.OrderBy(k => k.Key));
        }

        public Dictionary<char, int> CreateDictionary(string x)
        {
            Dictionary<char, int> d = new Dictionary<char, int>();
            for (int i = 0; i < x.Length; i++)
            {
                if (d.ContainsKey(x[i]))
                {
                    d[x[i]]++;
                }
                else
                {
                    d.Add(x[i], 1);
                }
            }

            return d;
        }
    }