# LeetCode -- 450. Delete Node in a BST (Medium)

    - given a root to a BST and the key int val 
    - delete the node with this val from the BST
    - return the root node
    - the root node might have changed

    - search for a node to delete
    - if found, delete the node

    - 3 deletion cases
        1. node is a leaf
        2. node has one child
        3. node has 2 children


# Primitive Solution - (Time: O(n), Space: O(n))



public class Solution {
    public TreeNode DeleteNode(TreeNode root, int key) {
        if (root == null) { return null; }
       
        if (root.val > key) { root.left = DeleteNode(root.left, key); }
        else if (root.val < key) { root.right = DeleteNode(root.right, key); }
        else
        {
            // Node to delete found
            // Case 1: No children (leaf node) or Case 2: One child
            if (root.left == null) return root.right;
            if (root.right == null) return root.left;

            // Case 3: Two children
            // Find the in-order successor (smallest in the right subtree)
            TreeNode successor = FindMin(root.right);
            root.val = successor.val; // Replace value with successor's value
            root.right = DeleteNode(root.right, successor.val); // Delete successor
        }

        return root;
    }

    private TreeNode FindMin(TreeNode node) {
        while (node.left != null) {
            node = node.left;
        }
        return node;
    }
}









