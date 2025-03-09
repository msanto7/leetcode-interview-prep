# LeetCode -- 872. Leaf-Similar Trees (Easy)

    - leaves have no children
    - a leaf sequence is the values of the leaf nodes in a binary tree from left to right
    - and a tree is leaf similar - if they share leaf sequences
    - so in this case we are given 2 different root nodes for 2 different trees and must return a boolean 
    - true - if the trees share the same leaf sequence

    - so I need to fully traverse both trees and compare each leaf to make sure they are equal in order
    - if node n -- n.right == null and n.left == null then we have a leaf of the tree

    - so one method that came to mind was...traverse the 1st tree and store the sequence in an array...do the same for the second tree...them compare the arrays
    - this seems pretty primitive...and traverses both trees separately...and uses 2 additional array/list variables
    - I am thinking there is a way to do this with both trees at the same time??
    - and to just compare each leaf as they come instead of storing the sequence...and short circuiting on the first mismatched leaf value
    - but whatever I am going to implement the first solution to start using depth first search and auxillary list variables
    
    - so now how do I optimize this...


# Recurisve Solution - (Time: O(n), Space: O(n))

    - here is my first succesful solution...just building lists for each leaf sequence and then comparing at the end
    - used recursion to traverse the trees


    public bool LeafSimilar(TreeNode root1, TreeNode root2) {

        List<int> r1Seq = new List<int>();
        List<int> r2Seq = new List<int>();

        FindLeafRec(r1Seq, root1);
        FindLeafRec(r2Seq, root2);

        // loop thru the lists and compare
        if (r1Seq.Count != r2Seq.Count) { return false; }
        
        for (int i = 0; i < r1Seq.Count; i++)
        {
            if (r1Seq[i] != r2Seq[i]) { return false; }
        }

        return true;
    }

    public void FindLeafRec(List<int> seq, TreeNode root)
    {
        if (root == null) { return; }
        else if (root.left == null && root.right == null)
        {
            seq.Add(root.val);
        }
        else if (root != null)
        {
            FindLeafRec(seq, root.left);
            FindLeafRec(seq, root.right);
        }
    }


