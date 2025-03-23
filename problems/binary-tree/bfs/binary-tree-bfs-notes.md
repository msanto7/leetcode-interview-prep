# Binary Tree - Breadth-First Search (BFS)

    - broad - this is going to traverse across width first
    - going level by level before getting deeper into the tree
    - 

    DFS vs. BFS -- https://www.youtube.com/watch?v=cS-198wtfj0&t=1s

# C#

    - implementation uses a queue to keep track of nodes at the current level before moving on
    - O(n) because each node is visited only once

    class Solution {
    public void BFS(TreeNode root) {
        if (root == null) return;

        Queue<TreeNode> queue = new Queue<TreeNode>();
        queue.Enqueue(root);

        while (queue.Count > 0) {
            TreeNode node = queue.Dequeue();
            Console.Write(node.val + " "); // Process node

            if (node.left != null) queue.Enqueue(node.left);
            if (node.right != null) queue.Enqueue(node.right);
        }
    }

    - 


## When to use

    - good for finding shortest paths
    - explores everything level by level
    - minimum depth of a binary tree
    - kth level or distance problems



    Final Thought:  When to Pick BFS vs. DFS?
    Scenario	                                        Use BFS?	    Use DFS?
    Level order traversal	                            ✅ Yes	        🚫 No
    Shortest path in an unweighted tree	                ✅ Yes	        🚫 No
    Finding the deepest node	                        ✅ Yes	        🚫 No
    Finding the longest path	                        🚫 No	        ✅ Yes
    Space efficiency matters	                        🚫 No	        ✅ Yes
    Solving tree-based DP problems	                    🚫 No	        ✅ Yes