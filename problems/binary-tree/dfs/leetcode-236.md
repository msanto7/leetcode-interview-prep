# LeetCode -- 236. Lowest Common Ancestor of a Binary Tree (Medium)

    - lowest common ancestor of a tree given two nodes and the root of the tree
    - so for nodes p and q...the LCA is the lowest node in the tree that has both p and q as descendants
    - a node is allowed to be a descendant of itself **
    - all node values are unique - * this is a good question to ask in an interview unless provided
    - the given nodes are guaranteed to exist in the tree
    
    - so I suppose the default LCA is always going to be the root of the tree
    - but working our way down we are going to have to keep some sort of track of the depth of each node
    - the depth of the LCA has to be >= the heighest common depth of p and q
    - that way the LCA node is either one of the two p or q...or a node above them
    - so how can we use DFS to find this node

    - so it seems like there are 2 scenarios
    - nodes are at the same level...and the LCA is the parent above
    - nodes are at different levels...and the LCA is one of the 2 nodes (obviously the higher one)
    - jk there is also the case where they are on separate levels but there is still a node above both that is the LCA because the higher node is not a parent of the other
    - so 3 scenarios
    - so if a node contains p and q in its sub tree...it could possible be the LCA...otherwise it is guarnateed NOT
    - if we call into the sub trees during the DFS...and get a non null response from both...that means p and q exist in the subtree of the current node...but I guess tht does mean it is the lowest common one...
    - 



# Recursive Solution - (Time: O(n), Space: O(n))


    public class Solution {
        public TreeNode LowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
            return DFS (root, p, q);
        }

        public TreeNode DFS(TreeNode curr, TreeNode p, TreeNode q)
        {
            if (curr == null || curr.val == p.val || curr.val == q.val) { return curr; }

            TreeNode left = DFS(curr.left, p, q);
            TreeNode right = DFS(curr.right, p, q);

            if (left != null && right != null)
            {
                return curr;
            }

            return left != null ? left : right;

        }
    }