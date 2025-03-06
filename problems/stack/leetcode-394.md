# LeetCode -- 394. Decode String (Medium)

    - alright so the premise is that we need to decode this string...repeating what is inside brackets k times
    - k[string]
    - would look like 2[abc] = abcabc
    - so need a stack to push and process the open and closing brackets
    - so the problem states that we do not have to deal with malformed strings

    - so we should iterate through the string and push onto the stack until we get to a ']' character
    - after looking through the example inputs..we need to be able to handle nested input...
    - so using a single stack is definitely going to have some nested loops in it...but I will continue working through that solution first
    
    - primitive solution wasn't too bad when you break down the scenarios
    - but ultimately it is a lot of nested looping

    - looks like there is a multiple stack solution...and also a recurive solution


# Primtive Solution - (Time: O(n), Space: O(n))

    public string DecodeString(string s) {

        Stack<char> st = new Stack<char>();
        StringBuilder sb = new StringBuilder();
        StringBuilder k = new StringBuilder();

        for (int i = 0; i < s.Length; i++)
        {
            if (s[i] == ']')
            {
                // then we should pop until we find the opening bracket and the num k
                // once we process that string...we need to push it on the stack and continue
                while (st.Count() > 0 && st.Peek() != '[')
                {
                    sb.Insert(0, st.Pop());
                }

                if (st.Peek() == '[') { st.Pop(); }

                // pop while we have a digit
                while (st.Count() > 0 && Char.IsNumber(st.Peek()))
                {
                    k.Insert(0, st.Pop());
                }

                var num = int.Parse(k.ToString());
                var s2 = sb.ToString();
                while (num > 0)
                {
                    for (int j = 0; j < s2.Length; j++)
                    {
                        st.Push(s2[j]);
                    }
                    num--;
                }
                
                sb.Clear();
                k.Clear();
            }
            else
            {
                st.Push(s[i]);
            }
        }

        while (st.Count() > 0)
        {
            sb.Insert(0, st.Pop());
        }

        return sb.ToString();
    }