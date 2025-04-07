# LeetCode -- 15. 3Sum (Medium)

    - integer array input
    - need to return a list of integer lists 
    - triplets where the values at the indices add up to zero
    
    - so I undersand the idea of fixing a number and then solving it as if it is two sum but I am not totally sure how to iterate through the array 
    - 



# Primitive Solution - (Time: O(n^2), Space: O(n))

    - had trouble getting through this on my own
    - had to consult the solutions...in theory it makes sense but still wasn't really clicking as to how to iterate through
    - so basically we are sorting the array...fixing numbers up to the first half of the array
    - and then handling it as if it is two sum by fixing the number we are at
    - and during our initial loop we are skipping duplicate values in the array
    - so O(nlogn) to sort the array...and we call our helper function basically n times



    public class Solution {
        public IList<IList<int>> ThreeSum(int[] nums) {
            List<IList<int>> trips = new List<IList<int>>();
            Array.Sort(nums);

            for (int i = 0; i < nums.Length && nums[i] <= 0; i++)
            {
                if (i == 0 || nums[i - 1] != nums[i])
                {
                    TwoSumII(nums, i, trips);
                }
            }
            
            return trips;
        }

        public void TwoSumII(int[] nums, int i, List<IList<int>> trips)
        {
            int lo = i + 1;
            int hi = nums.Length - 1;

            while (lo < hi)
            {
                int sum = nums[i] + nums[lo] + nums[hi];
                if (sum < 0)
                {
                    lo++;
                }
                else if (sum > 0)
                {
                    hi--;
                }
                else
                {
                    trips.Add(new List<int> { nums[i], nums[lo], nums[hi] });
                    lo++;
                    hi--;

                    while (lo < hi && nums[lo] == nums[lo - 1])
                    {
                        lo++;
                    }
                }
            }

        }
    }