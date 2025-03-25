# LeetCode -- 271. Encode and Decode Strings (Medium)

    - we are given a list of strings - and need to encode to a string
    - and then we decode it back to the original list
    - so my first thought is to use some type of strange character as our separator to tell whether we have a new string
    - but the string can contain any ascii characters 
    
    - so I get the idea of using something outside of the ascii character range as a delimeter...that is pretty easy and obvious
    
    - neetcodes video on this was very helpful
    - basically helps understand how to encode with the number length of a string and then a delimter
    - we then know regardless of if the delimeeter or the number are also in the string...that we can consistently decode
    

# Primitive Solution - (Time: O(n), Space: O(n))

    - this is the solution I implemented after looking through the neet code example briefly

    public class Codec {
        // Encodes a list of strings to a single string.
        public string encode(IList<string> strs) {
            string sb = "";
            foreach (var s in strs)
            {
                sb = sb + s.Length + "#" + s;
            }
            return sb;
        }

        // Decodes a single string to a list of strings.
        public IList<string> decode(string s) {
            List<string> l = new List<string>();
            int i = 0;
            while (i < s.Length)
            {
                int j = i;
                while (s[j] != '#')
                {
                    j++;
                }
                var stringLength = int.Parse(s[i..j]);
                l.Add(s.Substring(j + 1, stringLength));

                i = j + stringLength + 1;
            }

            return l;
        }
    }


















