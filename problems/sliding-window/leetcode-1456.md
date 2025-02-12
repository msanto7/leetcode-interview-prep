# LeetCode -- 1456. Maximum Number of Vowels in a Substring of Given Length (Medium)

    - so the length of the sub string is part of the input
    - we need to count the vowels in a substring so we need some concept of being a vowel (might try regex here)
    - we are returning the max count of vowels among those substrings in our input string
    - going to try to use another fixed sliding window approach



# Primitive Solution - (Time: O(n), Space: O(1))

    - first solution ended up working out here...probably a better way to do this adding in a hashmap maybe?
    - but this is the same concept as leetcode 643...fixed sliding window...we do sort of a presum..then process the new incoming and outgoing letter 1 step at a time as the window moves..updating the max count along the way

    public int MaxVowels(string s, int k) {
        int left = 0;
        int right = left + (k - 1);
        int numV = 0;
        int maxNumV = 0;

        // go through and count them up for the first substring
        for (int i = left; i < left + k; i++)
        {
            if (IsVowel(s[i])) { numV++; }
        }
        
        maxNumV = numV;
        left++;
        right++;

        // vowels - a, e, i, o, u
        while (right < s.Length)
        {
            if (IsVowel(s[left - 1])) { numV--; }
            if (IsVowel(s[right])) { numV++; }

            if (numV > maxNumV) { maxNumV = numV; }
            left++;
            right++;
        }
        
        return maxNumV;
    }

    public bool IsVowel(char c)
    {
        return (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') ? true : false;
    }





