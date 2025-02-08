
# LeetCode -- 238. Product of Array Except Self

    - so there are 2 caveats here that are important
    - 1st they explicitely mention to not use division which sort of takes you away from one of the first natural solutions
    - 2nd there is a follow up question about writing the solution using O(1) space -- so optimization is important

    - the general idea here is to recognize that what we need is a multiplication of the left and right prefix sums
    - and the optimization comes from doing 1 part of the prefix sum on the fly


    # Primitive Solution - (Time: O(n), Space: O(n))

        public class Solution {
            public int[] ProductExceptSelf(int[] nums) {      
                // O(n) time
                // cannot use division
                // alright so lets optimize        
                int[] left = new int[nums.Length];

                for (int i = 0; i < nums.Length; i++)
                {
                    if (i == 0) { left[i] = 1; }
                    else { left[i] = left[i - 1] * nums[i - 1]; }
                }

                int rightProd = 1;
                for (int i = nums.Length - 1; i >= 0; i--)
                {
                    left[i] = left[i] * rightProd;
                    rightProd = rightProd * nums[i];
                }

                return left;     
            }
        }



    # Optimized for O(1) Solution - (Time: O(n), Space: O(1))

        public class Solution {
            public int[] ProductExceptSelf(int[] nums) {      
                // O(n) time
                // cannot use division
                // alright so lets optimize        
                int[] left = new int[nums.Length];

                for (int i = 0; i < nums.Length; i++)
                {
                    if (i == 0) { left[i] = 1; }
                    else { left[i] = left[i - 1] * nums[i - 1]; }
                }

                int rightProd = 1;
                for (int i = nums.Length - 1; i >= 0; i--)
                {
                    left[i] = left[i] * rightProd;
                    rightProd = rightProd * nums[i];
                }

                return left;     
            }
        }







