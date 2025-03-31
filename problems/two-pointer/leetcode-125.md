# LeetCode -- 125. Valid Palindrome (Easy)

    - string input
    - palindrome is valid if after removing non alpha characters..and converting all to lower case...it reads the same way forward and backward
    
    - so regex to remove non alpha numeric characters
    - convert to lower case
    - push the first half into a hashset and then return false if 
    - ...ah jk order matters here
    - 


# Primitive Solution - (Time: O(n), Space: O(n))

    - quick solution with regex and string replace followed by looping pointers from both ends and comparing characters

    public bool IsPalindrome(string s) {
        var cleanS = Regex.Replace(s, "[^a-zA-Z0-9]", "");
        cleanS = cleanS.Replace(" ", "").ToLower();
        int i = 0;
        int j = cleanS.Length - 1;

        while (i < j)
        {
            if (cleanS[i] != cleanS[j]) { return false; }
            i++;
            j--;
        }
        
        return true;
    }
