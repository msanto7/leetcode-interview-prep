# LeetCode -- 394. Decode String (Medium)

    - alright so the premise is that we need to decode this string...repeating what is inside brackets k times
    - k[string]
    - would look like 2[abc] = abcabc
    - so need a stack to push and process the open and closing brackets
    - so the problem states that we do not have to deal with malformed strings

    - so we should iterate through the string and push onto the stack until we get to a ']' character
    - 


# Primtive Solution - (Time: O(n), Space: O(n))