# LeetCode -- 437. Path Sum III (Medium)

    - input is a root node and a target sum integer
    - need to return an integer number of the count of paths here the sum of the values is equal to the target
    - so we will at least have to visit each node once that is for sure
    - also the path can only travel from parent nodes to children ("downwards")
    - meaning we can't be going up and down levels to get the sum
    - the values can be negative - which would be a good thing to explicitly ask in a interview
    - think the concept with dfs is pretty simple here...so going to try to implement a recursive solution

    - meh i already see a flaw in my logic
    - if I am checking along a path that we have gone above the target sum...and lets say i am 3 nodes down
    - I can't reset and start at sum 0 from the current node...I would have to do so from node 2
    - so I need to be able to look back far enough somehow

    - so I ran into a problem with my solution
    - in one way i solved the look back problem by recalling my recursive function at each node
    - but now any good nodes below are potentially getting double triple...exponentially counted
    - so took a look at the editorial to get my bearings 
    - they are using a hashmap almost like a stack as they process through the tree

    - essentially we look back by assessing how many nodes = whatever the target sum is minus the current node value



# Recursive Solution - (Time: O(n^2) for unbalance tree O(Nlog(n) for balanced), Space: O(n))

    - had an annoying edge case test in leetcode where I had to change from int to long for the targetSum variable

    public class Solution {
        public int PathSum(TreeNode root, long targetSum) {
            if (root == null) { return 0; }
            return DFS(root, targetSum) + PathSum(root.left, targetSum) + PathSum(root.right, targetSum);
        }

        public int DFS(TreeNode node, long targetSum)
        {
            if (node.val == null) return 0;
            var numGood = (node.val == targetSum) ? 1 : 0;
            if (node.left != null) { numGood += DFS(node.left, targetSum - node.val); }
            if (node.right != null) { numGood += DFS(node.right, targetSum - node.val); }

            return numGood;
        }
    }


# Optimized Solution - (Time: O(n), Space: O(n))
PrefixSum and Hashmap approach get you to O(N) solution

    - prefix sum solution generated from copilot


    public class Solution {
        public int PathSum(TreeNode root, int targetSum) {
            // Dictionary to store the prefix sums and their counts
            var prefixSumCount = new Dictionary<long, int>();
            // Initialize with 0 sum to handle paths starting from the root
            prefixSumCount[0] = 1;

            return DFS(root, 0, targetSum, prefixSumCount);
        }

        private int DFS(TreeNode node, long currentSum, int targetSum, Dictionary<long, int> prefixSumCount) {
            if (node == null) {
                return 0;
            }

            // Update the current prefix sum
            currentSum += node.val;

            // Calculate the number of valid paths ending at the current node
            long targetPrefixSum = currentSum - targetSum;
            int numPaths = prefixSumCount.ContainsKey(targetPrefixSum) ? prefixSumCount[targetPrefixSum] : 0;

            // Update the prefix sum count for the current sum
            if (!prefixSumCount.ContainsKey(currentSum)) {
                prefixSumCount[currentSum] = 0;
            }
            prefixSumCount[currentSum]++;

            // Recurse into the left and right subtrees
            numPaths += DFS(node.left, currentSum, targetSum, prefixSumCount);
            numPaths += DFS(node.right, currentSum, targetSum, prefixSumCount);

            // Backtrack: remove the current sum from the prefix sum count
            // to avoid affecting other paths
            prefixSumCount[currentSum]--;
            if (prefixSumCount[currentSum] == 0) {
                prefixSumCount.Remove(currentSum);
            }

            return numPaths;
        }
    }








