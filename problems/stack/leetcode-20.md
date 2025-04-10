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


# Primtive Solution - (Time: O(n^2), Space: O(n))

    - 








    