# LeetCode -- 20. Valid Parentheses (Easy)

    - alright so we are given a string of only (, [, or { and there closing counter parts
    - we need to validate 3 criteria
        - open brackets must be closed by their same type
        - the brackets must be closed in the correct order
        - every closed bracket must have a corresponding open bracket of the same type

    - so this is supposed to be a stack problem
    - I suppose i can push each opening bracket into the stack
    - pop when there is a closing one...and if it doesn't match in type...return false
    - btw we are just returning a boolean value
    - if they do match up i can continue iterating until the stack is empty
    - if stack is empty and string is not done iterating...return false


# Primtive Solution - (Time: O(n), Space: O(n))

    - here is my first terribly implemented stack solution
    - I kept having one off issues for edge cases and things i just ignored at first
    - i will really need to pay attention to those things while i am solving these eeven just on my own
    - there is a way to improve this with a dictionary mapping the types of brakcets to there closing counterpart instead of my if statements
    - also we might as well use a for loop because if valid we need to iterate through everything
    - and if not the while loop conditrion still isn't determing valid anyway

    public bool IsValid(string s) {
        Stack<char> stack = new Stack<char>();
        int i = 1;

        if (s.Length <= 1) { return false; }
        if (s[0] == '(' || s[0] == '{' || s[0] == '[')
        {
            stack.Push(s[0]);
        }
        else 
        {
            return false;
        }

        while (i < s.Length)
        {
            if (s[i] == '(' || s[i] == '{' || s[i] == '[')
            {
                stack.Push(s[i]);
            }
            else
            {
                if (stack.Count() == 0) {return false; }
                else
                {
                    var open = stack.Pop();
                    if (open == '(' && s[i] != ')') { return false; }
                    else if (open == '{' && s[i] != '}') { return false; }
                    else if (open == '[' && s[i] != ']') { return false; }
                }
            }

            i++;
        }

        return stack.Count() == 0 && i == s.Length ? true : false;
    }








