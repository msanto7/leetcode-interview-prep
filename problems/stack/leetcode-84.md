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

    - after a bit i ended up just watching the neetcode video
    - in general the implementation makes sense
    - i need to get better at exploring the intuition and moving that into a solution 

# Primtive Solution - (Time: O(n), Space: O(n))

    - this solution is one single pass with a stack and uses the idea of computing left and right max areas without having to loop them individually
    - the intuition is that when the next height is less than the current...that we can't move more to the right in terms of that max height...so we need to look backcwards to compute the potentially area...update the max...and then continue

    public int LargestRectangleArea(int[] heights) {
        int maxArea = 0;
        Stack<(int, int)> s = new Stack<(int, int)>(); // value tuple - (index, current height)
        if (heights.Length == 1) { return heights[0]; }

        for (int i = 0; i < heights.Length; i++)
        {
            int start = i;
            while (s.Count > 0 && s.Peek().Item2 > heights[i])
            {
                var top = s.Pop();
                int index = top.Item1;
                int height = top.Item2;
                maxArea = Math.Max(maxArea, height * (i - index));
                start = index;
            }
            s.Push((start, heights[i]));
        }

        foreach (var pair in s)
        {
            int index = pair.Item1;
            int height = pair.Item2;
            maxArea = Math.Max(maxArea, height * (heights.Length - index));
        }
        return maxArea;
    }






