# LeetCode -- 104. Maximum Depth of Binary Tree (Easy)

    - alright so we are using depth first search technique heree
    - we are given a tree node
    - the tree is binary
    - and we need to determine the number of nodes along the longest path from the root node down to the farthest leaf node

    - so I am not yet sure how the traversal types (pre, in, and post) come into play here
    - I imagine it doesn't matter in this case potentially
    - recursive or iterative solution is probably more relevant here
    - I am going to try the recursive solution first because it seems to make the most sense to me right now
    - 

# Recurisve Solution - (Time: O(n), Space: O(n))

    - so this is the first solution i came up with that is recursive and fairly intuitive
    - I have a quick refactor below though...that removes the unecessary helper method I added


    public class Solution {
        public int MaxDepth(TreeNode root) {
            if (root == null) { return 0; }
            else
            {
                return Rec(root, 0);
            }
        }

        public int Rec(TreeNode root, int depth)
        {
            if (root == null) { return depth; }
            else
            {
                return Math.Max(Rec(root.left, depth + 1), Rec(root.right, depth + 1));
            }
        }
    }



    // *****************************************************************
    public int MaxDepth(TreeNode root) {
        if (root == null) { return 0; }
        else
        {
            int leftH = MaxDepth(root.left);
            int rightH = MaxDepth(root.right);
            return 1 + Math.Max(leftH, rightH);
        }
    }



