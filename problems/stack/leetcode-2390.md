# LeetCode -- 2390. Removing Stars From a String (Medium)

    - 1 string as input and 1 string as output
    - remove a star...and the closest non-star character to the left
    - return the string once all the stars have been removed
    
    - so this should be a stack problem...can iterate through the string...fill a stack
    - and pop the last item when a star is found



# Optimized Solution - (Time: O(n), Space: O(n))

    - so this was definitely a miss labeled medium problem
    - can be solved with strings, two pointers, stacks
    - here is a basic stack solution


    public string RemoveStars(string s) {
        Stack<char> result = new Stack<char>();

        for (int i = 0; i < s.Length; i++)
        {
            // if we have a star...pop
            if (s[i] == '*') { result.Pop(); }
            else { result.Push(s[i]); }
            // if non star...push on the stack
        }

        return string.Concat(result.ToArray().Reverse()).ToString();
    }


