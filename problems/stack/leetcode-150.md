# LeetCode -- 150. Evaluate Reverse Polish Notation (Medium)

    - we are given an array of strings
    - each string is a token that represents a math expression
    - so operators follow operands in this notation
    - also known as postfix notation
    - we need to evaluate the expression and return an integer answer
    
    - 4 valid operators
        - +, -, *, /
    - no division by zero
    - input is guarnteed to valid
    
    - so this lends itself to a stack because we can push the integers onto the stack until we come across an operator...then we can pop and apply the operator...then push the result back to the stack until we are all the way thru the strings
    - 


# Primtive Solution - (Time: O(n), Space: O(n))

    - this was my first accepted answer...only took me about 15 minutes without help
    - followed the general idea above...push nums...evaluate operands...and push result
    - one optimization or atleast thing to mention in an interview would be that I could create a dictionary of strings and there actual operator functions instead of the simple if statements
    

    public int EvalRPN(string[] tokens) {
        Stack<int> s = new Stack<int>();

        foreach (string item in tokens)
        {
            // push if it can be evaluated as a num
            if (int.TryParse(item, out int result))
            {
                s.Push(result);
            }
            // otherwise we need to pop and evaluate (always pop 2 nums in this case)
            else
            {
                var op1 = s.Pop();
                var op2 = s.Pop();

                if (item == "+") { s.Push(op1 + op2); }
                else if (item == "-") { s.Push(op2 - op1); }
                else if (item == "*") { s.Push(op1 * op2); }
                else if (item == "/") { s.Push(op2 / op1); }
            }            
        }

        return s.Pop();
    }













