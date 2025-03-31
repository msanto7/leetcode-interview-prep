# LeetCode -- 167. Two Sum II - Input Array Is Sorted (Medium)

    - integer array and target integer as input
    - array is sorted in non-decreasing order
    - only one solution
    - can't use the same element twice
    - solution can only use constant extra space
    - returning an integer array of the indices of the array elements that sum to the target
    
    - so there has to be a two pointer solution that can do this efficiently
    - 


# Primitive Solution - (Time: O(n), Space: O(n))

    - took me a longer time because i ended up in a nested if statement rabbit whole and started the right side point incorrectly but here is the simple solution

    public int[] TwoSum(int[] numbers, int target) {
        int left = 0;
        int right = numbers.Length - 1;

        while (left < right)
        {
            if (numbers[left] + numbers[right] == target)
            {
                return new int[] { left + 1, right + 1 };
            }
            else if (numbers[left] + numbers[right] < target)
            {
                left++;
            }
            else
            {
                right--;
            }
        }
        return new int[] { left, right };
    }