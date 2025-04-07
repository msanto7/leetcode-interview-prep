# LeetCode -- 42. Trapping Rain Water (Hard)

    - input is an integer array of heights
    - elevation map with width of each bar = 1
    - compute how much rain water it can trap
    - we are returning an integer for units of rain water that are trapped

    - once again a two pointer problem
    - seems like it would make sense to do sort of a sliding window where we calculate each section of trapped water until it is closed off...then move to the next section
    - 

# Primitive Solution - (Time: O(n^2), Space: O(n))