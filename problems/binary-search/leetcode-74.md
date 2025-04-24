# LeetCode -- 74. Search a 2D Matrix (Medium)

    - given 2d array matrix and a target integer value
    - each row is sorted in non-decreasing order
    - first int of each row is greater than the last of the prev row
    - we are just returning a boolean as to whether or not the target exists in the matrix
    - but we need to accomplish it in O(log(m * n)) time...so binary search comes into play
    - just need to contend with the rows instead of a flat array
    - probably both an iterative and recursive solution here...going to take a stab at the iterative first
    
    - so I can add the midpoint for the columns i suppose...and then determine each time if it is in that specific row
    - wondering if I can first find the row...then find the column if possible

# Primitive Solution - (Time: O(log(m * n)), Space: O(n))

    - came up with my own solution for this...found the column first using binary search...
    - then searched within that row
    - I used 2 separate loops so there is defninitely an optimization or atleast way to cleaan this up

    public class Solution {
        public bool SearchMatrix(int[][] matrix, int target) {
            int leftR = 0;
            int rightR = matrix.Length - 1;
            int row = -1;
            int left = 0;
            int right = matrix[0].Length - 1;

            // find the row first
            while (leftR <= rightR)
            {
                int midRow = leftR + (rightR - leftR) / 2;
                if (target > matrix[midRow][right])
                {
                    leftR = midRow + 1;
                }
                else if (target < matrix[midRow][left])
                {
                    rightR = midRow - 1;
                }
                else
                {
                    row = midRow;
                    break;
                }
            }

            if (row == -1) { return false; }

            // search within the row
            while (left <= right)
            {
                int mid = left + (right - left) / 2;
                if (target > matrix[row][mid])
                {
                    left = mid + 1;
                }
                else if (target < matrix[row][mid])
                {
                    right = mid - 1;
                }
                else
                {
                    return true;
                }
            }

            return false;
        }
    }