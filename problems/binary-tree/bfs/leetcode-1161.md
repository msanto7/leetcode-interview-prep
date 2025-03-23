# LeetCode -- 1161. Maximum Level Sum of a Binary Tree (Medium)

    - input is the root of a binary tree
    - max sum with min level
    - I basically used the same basic BFS implementation i did before...
    - just instead I sum each val across levels...and when we switched levels i would push the last one to a dictionary
    - which I used to keep track of the sums at each level to find the max quickly later with linq



# Primitive Solution - (Time: O(n), Space: O(n))

    - here is my intitial solution I came up with


    public int MaxLevelSum(TreeNode root) {
        Dictionary<int, int> levelSum = new Dictionary<int, int>();
        Queue<Tuple<TreeNode, int>> q = new Queue<Tuple<TreeNode, int>>();
        int currSum = 0;

        q.Enqueue(new Tuple<TreeNode, int>(root, 1));
        var curr = new Tuple<TreeNode, int>(root, 1);
        var prev = new Tuple<TreeNode, int>(root, 1);
        int i = 1;

        while(q.Any())
        {
            prev = curr;
            curr = q.Dequeue();
            i = curr.Item2;
            if (curr.Item2 == prev.Item2) { currSum += curr.Item1.val; }
            else
            {
                levelSum.Add(prev.Item2, currSum);
                currSum = curr.Item1.val;
            }            

            if (curr.Item1.left != null) { q.Enqueue(new Tuple<TreeNode, int>(curr.Item1.left, i + 1)); }
            if (curr.Item1.right != null) { q.Enqueue(new Tuple<TreeNode, int>(curr.Item1.right, i + 1)); }
        }

        levelSum.Add(curr.Item2, currSum);

        return levelSum.OrderByDescending(x => x.Value).First().Key;
    }















