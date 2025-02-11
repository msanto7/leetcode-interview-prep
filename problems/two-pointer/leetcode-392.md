
# LeetCode -- 392. Is Subsequence (Easy)
    - solved this one pretty quick
    - knowing it was a two pointer helped but ultimately was a fairly simple idea



# Primitive Solution - (Time: O(n), Space: O(1))

    public bool IsSubsequence(string s, string t) {
            int pS = 0;
            int pT = 0;

            while(pS < s.Length && pT < t.Length)
            {
                if (s[pS] == t[pT])
                {
                    pS++;
                    pT++;
                }
                else
                {
                    pT++;
                }
            }
            return (pS == s.Length ? true : false);
    }

# Optimized Solution - (Time: O(n), Space: O(1))

    - so there is a greedy style solution with a hashmap that maybe I will come back to understand better