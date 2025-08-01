# LeetCode -- 875. Koko Eating Bananas (Medium)

    - so eat all the bananas as slow as possible is the goal
    - guard comes back in h hours
    - the value at each integer array index is the amount of bananas in that pile
    - so I guess we could just iterate through the integers starting with the lowest valuee in the array?
    - but how do we determine without bruteforce checking everything
    - the total bananas across all piles has to be of some use
    - but the distribubtion matters for sure 
    - i guess it is worth noting we are looking at the piles as if she an go from one to any other the order doesn't matter
    - but if we did order them, we could binary search testing the bananas per hour more quickly
    - so we run thru and figure out how many multiples of k we can eat until it surpasses the hours h
    - but we also need to optimize it
    - so we could use the bianry search for the selection of k
    - then loop thr and calculate how long it would take to use that

# Primitive Solution - (Time: O(log(m * n)), Space: O(n))

    public class Solution {
        public int MinEatingSpeed(int[] piles, int h) {
            int left = 1;  // Minimum possible eating speed
            int right = piles.Max();  // Maximum eating speed needed
            
            while (left < right) {
                int mid = left + (right - left) / 2;
                
                if (CanFinish(piles, mid, h)) {
                    right = mid;  // Try slower speed
                } else {
                    left = mid + 1;  // Need faster speed
                }
            }
            return left;
        }

        private bool CanFinish(int[] piles, int speed, int h) {
            int hours = 0;
            foreach (int pile in piles) {
                hours += (int)Math.Ceiling((double)pile / speed);
                if (hours > h)
                {
                    return false;
                }
            }
            return true;
        }
    }

# Speed Calculation Explained

## Why Math.Ceiling?
    - Koko can only eat during discrete hours (1 hour, 2 hours, etc.)
    - She can't eat partial hours, so we must round UP to next whole hour
    
## Examples:
    - Pile = 10 bananas, Speed = 3 bananas/hour
    - Time needed = 10 ÷ 3 = 3.33... hours
    - Since she can't eat for partial hours, she needs 4 full hours
    - Math.Ceiling(3.33) = 4

    - Pile = 9 bananas, Speed = 3 bananas/hour  
    - Time needed = 9 ÷ 3 = 3.0 hours (exact)
    - Math.Ceiling(3.0) = 3

## Step-by-step for piles = [3,6,7,11], speed = 4:
    - Pile 3: Math.Ceiling(3/4) = Math.Ceiling(0.75) = 1 hour
    - Pile 6: Math.Ceiling(6/4) = Math.Ceiling(1.5) = 2 hours  
    - Pile 7: Math.Ceiling(7/4) = Math.Ceiling(1.75) = 2 hours
    - Pile 11: Math.Ceiling(11/4) = Math.Ceiling(2.75) = 3 hours
    - Total: 1 + 2 + 2 + 3 = 8 hours

## Alternative calculation (without Math.Ceiling):
    ```csharp
    hours += (pile + speed - 1) / speed;  // Integer division trick
    ```
    This works because: (pile + speed - 1) / speed = ceiling(pile / speed)




