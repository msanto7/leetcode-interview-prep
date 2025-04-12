# LeetCode -- 739. Daily Temperatures (Medium)

    - alright so we are given an array if integer temperatures
    - represent the daily temperatur of onsecutive days
    - we need to return an array of integers where the index is the amount of days until a day warmer than the curent
    
    - so the right most will alwasys be 0...because there is no days after from the perspective of this array
    - every other index in the result array could be >= 0
    - i feel like this could have a 2 pointer solution but this comes from the neetcode array category so we are going to try to implement with an array
    - so we need to be able to look back from each number until we get an answer
    - so push nums onto the stacck from left to right inthe array
    - 


# Primtive Solution - (Time: O(n), Space: O(n))

    - had trouble getting to this answer
    - needed to push more than just the temp to the stack...because the index is needed for each
    - so the stack ends up being monotonic decreasing order
    - we are also benefiting from c# defaulting all int arra value to zero...because we technically leave the stack full of the ones that never have a greater temp
    - https://neetcode.io/solutions/daily-temperatures

    public int[] DailyTemperatures(int[] temperatures) {
        Stack<(int, int)> s = new Stack<(int, int)>(); // (temp, index)
        int[] result = new int[temperatures.Length];
        result[temperatures.Length - 1] = 0;

        if (result.Length == 1) { return result; }

        for (int i = 0; i < temperatures.Length; i++)
        {
            int t = temperatures[i];

            while (s.Count > 0 && t > s.Peek().Item1)
            {
                var pair = s.Pop();
                result[pair.Item2] = i - pair.Item2;
            }
            s.Push((t, i));
        }
        
        return result;
    }