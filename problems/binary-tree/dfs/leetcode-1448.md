# LeetCode -- 1448. Count Good Nodes in Binary Tree (Medium)

    - we are given the root node of a binary tree
    - we are returning a count of what is considered a "good" node
    - a good node is defined as one where you can make it to the node from the root without encountering a node value greater than the destination node value

    - so basically at each node...if the path there has a value greater than it...it is not counted as good
    - I almost feel like using a stack and traversing the tree while pushing the values on the stack helps keep track of the values inbeteen X and the root
    - I think I am going to try to traverse the tree like normal recursive DFS
    - so the idea is that whatever node i am at...if it is less than the root or an node inbetween...then it is not a good node
    
    - I had trouble getting to the exact recursive solution but it makes sense easily after loooking through it
    - I am going to implement the iterative solution for this problem as well so I am exposed to how that works


# Recursive Solution - (Time: O(n), Space: O(n))

    public class Solution {
        private int numGood = 0;
        public int GoodNodes(TreeNode root) {
            DFS(root, Int32.MinValue);
            return numGood;
        }

        public void DFS(TreeNode node, int maxPath)
        {
            if (node.val >= maxPath) { numGood++; }

            if (node.right != null) { DFS(node.right, Math.Max(node.val, maxPath)); }

            if (node.left != null) { DFS(node.left, Math.Max(node.val, maxPath)); }
        }
    }


# Iterative Solution - (Time: O(n), Space: O(n))

    - so for the iterative solution we need to implement a stack to keep track of the calls
    - we are essentially imitating the call stack from the recursive solution

    






