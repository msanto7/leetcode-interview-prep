
# LeetCode -- 334. Increasing Triplet Subsequence (Medium)

    - so there is a follow up about O(n) time and O(1) space
    - i also noticed that we can have negative values
    - we are returning a boolean
    - asking if the sequence of indicies needs to be consequtive would be a good clarifying question
    - two pointer comes to mind for a potential solution with O(1) space

    - so after reading through the editorial...the general solution has to do with the fact the we just need to know and increasing subsequence exists in general
    - so we can scan through the array...save the smallest...and second smallest elements in order as we go...and then we fall into our else case when a number large then those 2 exists...and there we go...we have the sequence


    # Primitive Solution - (Time: O(n), Space: O(n))


    # Optimized Solution - (Time: O(n), Space: O(1))

        public class Solution {
            public bool IncreasingTriplet(int[] nums) {

                int first = Int32.MaxValue;
                int second = Int32.MaxValue;
                int n = nums.Length;

                for (int i = 0; i < n; i++)
                {
                    // check for smallest number
                    if (nums[i] <= first) { first = nums[i]; }
                    // check for second smallest
                    else if (nums[i] <= second) { second = nums[i]; }
                    else { return true; }
                }

                return false;
            }
        }












