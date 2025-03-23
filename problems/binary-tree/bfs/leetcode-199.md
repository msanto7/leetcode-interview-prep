# LeetCode -- 199. Binary Tree Right Side View (Medium)

    - input is the root node of a binary tree
    - need to imagine we are standing on the right side of the tree
    - what nodes can we see ordered from top to bottom
    - so we are sort of looking for the right most node at each level because that is the one that we will see
    - we are returning a list of integers
    - which is the value of all of the notes in order from top to bottom
    - so the root node will always be on the list
    - so I think I am just going to implement the queue style BFS and instead just skip to the last of eah level add it to the list...then move on



# Primitive Solution - (Time: O(n), Space: O(n))

    - this is the first solution i came up with
    - essentially just breadth first search with a level tracking to see when we are at the end of a level...because we are moving left to right so this will be all the visible nodes
    - for the last node we always add it because it will either be on a new level by itself or the right most node of its level


    public IList<int> RightSideView(TreeNode root) {
        Queue<Tuple<TreeNode, int>> q = new Queue<Tuple<TreeNode, int>>();
        List<int> l = new List<int>();
        if (root == null) { return l; }

        // push the root and begin processing
        q.Enqueue(new Tuple<TreeNode, int>(root, 0));
        TreeNode prev;
        int i = 0;
        var curr = new Tuple<TreeNode, int>(root, 0);

        while (q.Any())
        {
            prev = curr.Item1;
            curr = q.Dequeue();
            if (curr.Item2 != i) { l.Add(prev.val); }
            i = curr.Item2;
            if (curr.Item1.left != null) { q.Enqueue(new Tuple<TreeNode, int>(curr.Item1.left, i + 1)); }
            if (curr.Item1.right != null) { q.Enqueue(new Tuple<TreeNode, int>(curr.Item1.right, i + 1)); }
        }

        l.Add(curr.Item1.val);
        return l;
    }