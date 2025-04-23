# LeetCode -- 84. Largest Rectangle in Histogram (Hard)

    - given an integer array of integers representing heights
    - the width of each bar is 1
    - we are returning the area of the largest rectangle in the histogram
    
    - so this appears as not being that difficult
    - but I am trying to think of how to use a stack...and how this would be a hard level question
    - so we are trying to maximize the length and width together
    - so there has to be some combination of things we can push on the stack
    - let me just talk through what my intuitive process of finding the answer is
    - in general I am scanning and comparing all possible areas while keeping track of a max
    - I am thinking i can loop...and calculate the area at each position along with the minimum 
    - okay jk so I feel like i understand maybe...
    - if I push all of the array items on a stack... then pop and calculate area
    - meh...its like you need to keep track of the max common height of the 1 or 2 adjacent items to each item
    - alright so after looking at neetcode hints I think I am on the right track
    - need to compute right and left areas potentially from each item
     


# Primtive Solution - (Time: O(n), Space: O(n))

    - 






