# LeetCode -- 1372. Longest ZigZag Path in a Binary Tree (Medium)

    - input is the root of a binary tree
    - we are returning an integer referred to as the zigzag length (number of nodes visited)
    - single node length is 0
    - need to return the longest zigzag path in the tree

    - zig zag path is defined as 
        - choosing any node in a binary tree...and a direction (left or right)
        - if current direction is right...move right...otherwise move left
        - swap direction and repeat until you cannot move anymore

    - so this is a longest path question
    - wondering if there is a way to do this without processing every single node with each starting direction and maintaining a max sum
    - so maybe i will start by implementing the strategy above and then trying to optimize



# Recursive Solution - (Time: O(n2), Space: O(n))

    - so I implemented this solution but it was timing out because it literally iterates and finds the left and right zig zags for every single node instead of optimizing and paying attention to nodes we already calculated
    - going to read through the editorial and see what other options are out there
    - 



    public class Solution {
        public int LongestZigZag(TreeNode root) {
            TreeNode curr = root;        
            return DFS(root);
        }

        public int DFS(TreeNode node)
        {
            var longestZag = 0;
            longestZag = Math.Max(ZigZag(node, true), ZigZag(node, false));

            if (node.right != null)
            {
                longestZag = Math.Max(DFS(node.right), longestZag);
            }
            if (node.left != null)
            {
                longestZag = Math.Max(DFS(node.left), longestZag);
            }

            return longestZag;
        }

        public int ZigZag(TreeNode node, bool right)
        {
            if (right && node.right != null)
            {
                return 1 + ZigZag(node.right, false);
            }
            if (!right && node.left != null)
            {
                return 1 + ZigZag(node.left, true);
            }

            return 0;
        }
    }


# Optimized Solution - (Time: O(n), Space: O(n))

    - so in general my solution was on track...but i needed to combine the methods to avoid the double recursion 
    - this solution handles starting at a new node inline based on the right/left condition so we only touch each node once technically


    public class Solution {
        public int LongestZigZag(TreeNode root) {
            TreeNode curr = root;        
            return DFS(root, true, 0, 0);
        }

        public int DFS(TreeNode node, bool right, int zagCount, int longestZag)
        {
            if (node == null) { return longestZag; }

            longestZag = Math.Max(zagCount, longestZag);

            if (right)
            {
                longestZag = Math.Max(DFS(node.right, false, zagCount + 1, longestZag), DFS(node.left, true, 1, longestZag));
            }
            else
            {
                longestZag = Math.Max(DFS(node.left, true, zagCount + 1, longestZag), DFS(node.right, false, 1, longestZag));
            }

            return longestZag;
        }
    }






