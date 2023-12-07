
// ****************** INTERVIEW PREP NOTES ***************

## LeetCode #88 - Merge Sorted Array
    - https://leetcode.com/problems/merge-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150

    Solution 1 - merge first then sort 
        - so this solution just merges the values from nums2 into nums1
        - then uses a built in algorithm to sort the array in place

        public class Solution {
            public void Merge(int[] nums1, int m, int[] nums2, int n) {        
                
                // no return -- just altering nums1 array
                for (int i = 0; i < n; i++)
                {
                    nums1[m] = nums2[i];
                    m++;
                }
                
                // sort the array
                Array.Sort(nums1);
            }
        }

    Solution 2 - Three pointer (start from beginning)
        - this essentially just avoids having to do the sort in place
        - but it does duplicate the array..so not really good for space savings


