# LeetCode -- 700. Search in a Binary Search Tree (Easy)

    - given the root of a tree and an integer
    - need to find the node in the BST thats value is equal to the given int
    - return the node
    - return null if it is not found



# Primitive Solution - (Time: O(n), Space: O(n))

    - this is the first solution I came up with

    public TreeNode SearchBST(TreeNode root, int val) {

        var curr = root;

        while (curr != null)
        {
            if (curr.val < val)
            {
                curr = curr.right;
            }
            else if (curr.val > val)
            {
                curr = curr.left;
            }
            else
            {
                return curr;
            }
        }
        
        return null;
    }

# Recursive Solution - (Time: O(n), Space: O(n))

    - 



    public TreeNode SearchBST(TreeNode root, int val) {
        // Base case: if the root is null or the value matches the current node
        if (root == null || root.val == val) {
            return root;
        }

        // Recur into the left or right subtree based on the value
        return val < root.val ? SearchBST(root.left, val) : SearchBST(root.right, val);
    }









