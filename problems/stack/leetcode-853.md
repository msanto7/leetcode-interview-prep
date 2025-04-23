# LeetCode -- 853. Car Fleet (Medium)

    - alright so we are given an integer target mile for n cars at various positions from the starting mile 0
    - also given 2 integer arrrays, 1 for speed and 1 for position between mile 0 and target (both length n)
    - the index refers to a specific car
    - a car cannot pass another...but it can catch up and then travel next to a slower car at their speed
    - a car fleet is a car or car driving next to each other
    - speed of the car fleet is the minimum speed of the group of cars
    - i need to return the number of car fleets or groups that will make it to the target mile
    
    - so I i need to keep track of the cars as unit of time pass...and combine them into a fleet with 1 speed
    - I feel like I can use a stack...of maybe a position and a speed...and update them until they hit the target position
    - maybe keeping a count or something until the stack is empty
    - i am also thinking for optimizing...is there a way to not process every car to the target...but actually that doesn't really matter necessarily...could still get an O(n) solution if a car starts at 0 and is speed 1
    - as far as edge cases speed is not allowed to be <= 0 so we are good there
    - 


# Primtive Solution - (Time: O(nlogn), Space: O(n))

    - could not have come up with this on my own at the moment...but it makes sense
    - the formula for time to get to the target is crucial here...along with descending order sort
    - we figure out if a car is going to catch up to another by whether or not there time is equal or greater than the car in front of it
    - and then we pop the cars where this is the case...representing adding this car to the 'fleet'
    - so the count remaining in the stack at the end is the final count of fleets


    public int CarFleet(int target, int[] position, int[] speed) {
        Stack<decimal> s = new Stack<decimal>();
        int[][] positionSpeed = new int[position.Length][];

        // fill array with speed and position for each car at each index
        for (int i = 0; i < position.Length; i++)
        {
            positionSpeed[i] = new int[] { position[i], speed[i] };
        }

        // sort the array by position
        Array.Sort(positionSpeed, (x, y) => y[0].CompareTo(x[0]));

        foreach (var x in positionSpeed)
        {
            s.Push((decimal)(target - x[0]) / x[1]);
            if (s.Count >= 2 && s.Peek() <= s.ElementAt(1))
            {
                s.Pop();
            }
        }
        return s.Count;
    }