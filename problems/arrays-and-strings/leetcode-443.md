# LeetCode -- 443. String Compression (Medium)

    - so right off the bat I have to atleast traverse the array 1 time
    - I need some sense of what the previous character is...and a count associated to that character
    - they are asking for constant extra space so we should be modifying the input array in place
    - so I have a relatively close solution...but I am just having trouble handling the last character situation
    - because we have to look back essentially to see what is next



# Primitive Solution - (Time: O(nlog(n)), Space: O(n))

    - so I wrote this really bad solution but it does work at the moment
    - i pass through the array 1 time...while keeping track of the prev character...and the count of 
    - how many times it has been seen...and the total count which is used to iterate through the array and do the rewriting
    - there is a nested loop in here that...but it doesn't make it O(n^2) time complexity... I would imagine it is in between

        public class Solution {
            public int Compress(char[] chars) {
                int totalCount = 0;
                int charCount = 1;
                char prev = chars[0];

                if (chars.Length == 1) { return 1; }

                for (int i = 1; i < chars.Length; i++)
                {
                    // case for when the character changes
                        // only 1 chacter - just add char
                        // > 1 count - add char and count num as string
                    if (chars[i] != prev)
                    {
                        if (charCount == 1)
                        {
                            chars[totalCount] = prev;
                            totalCount++;
                            prev = chars[i];
                            charCount = 1;
                        }
                        else
                        {
                            // handle int to string and what not
                            chars[totalCount] = prev;
                            totalCount++;
                            prev = chars[i];                

                            // var digits = charCount.ToString().Select(x => int.Parse(x.ToString())).ToArray();
                            var numString = charCount.ToString();
                            foreach (char c in numString)
                            {
                                chars[totalCount] = c;
                                totalCount++;
                            }
                            charCount = 1;
                        }
                    }

                    // case for when the character stays the same
                    else if (chars[i] == prev)
                    {
                        charCount++;
                    }
                }

                if (charCount == 1)
                {
                    chars[totalCount] = prev;
                    totalCount++;
                }
                else
                {
                    // handle int to string and what not
                    chars[totalCount] = prev;
                    totalCount++;               

                    // var digits = charCount.ToString().Select(x => int.Parse(x.ToString())).ToArray();
                    var numString = charCount.ToString();
                    foreach (char c in numString)
                    {
                        chars[totalCount] = c;
                        totalCount++;
                    }
                }
                
                return totalCount;
            }
        }

# Primitive Solution #2 - (Time: O(nlog(n)), Space: O(n))
    - pretty much the same solution as above...just refactored to remove some repeated code


        public class Solution {
            public int Compress(char[] chars) {
                int totalCount = 0;
                int charCount = 1;
                char prev = chars[0];

                if (chars.Length == 1) { return 1; }

                for (int i = 1; i < chars.Length; i++)
                {
                    // case for when the character changes
                        // only 1 chacter - just add char
                        // > 1 count - add char and count num as string
                    if (chars[i] != prev)
                    {
                        chars[totalCount] = prev;
                        totalCount++;
                        prev = chars[i];
                        
                        if (charCount > 1)
                        {
                            var numString = charCount.ToString();
                            foreach (char c in numString)
                            {
                                chars[totalCount] = c;
                                totalCount++;
                            }
                        }

                        charCount = 1;
                    }

                    // case for when the character stays the same
                    else if (chars[i] == prev)
                    {
                        charCount++;
                    }
                }

                chars[totalCount] = prev;
                    totalCount++;

                if (charCount > 1)
                {
                    var numString = charCount.ToString();
                    foreach (char c in numString)
                    {
                        chars[totalCount] = c;
                        totalCount++;
                    }
                }
                
                return totalCount;
            }
        }


# Optimized Solution - (Time: O(n), Space: O(1))





