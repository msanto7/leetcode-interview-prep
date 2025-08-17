# Leetcode - 33. Search in Rotated Sorted Array (Medium)

    - another pivoted sorted array
    - so now we are searching for the index of a specific targeted integer value
    - if the target is not in the array just return -1
    - 

# Primitive Solution - (Time: O(n), Space: O(n))

    - this was my first try still failing one of the cases right now
    - I am skipping over the target value with my current logic...I need to handle the left side better somehow...I also feel like the pivot is off

    public int Search(int[] nums, int target) {
        int left = 0;
        int right = nums.Length - 1;

        while (left < right)
        {
            var mid = left + (right - left) / 2;
            if (nums[mid] == target) { return mid; }
            if (nums[left] == target) { return left; }
            if (nums[right] == target) { return right; }
            if (nums[left] >= nums[right] && target > nums[left] && target < nums[right])
            {
                left = mid + 1;
            }
            else
            {
                right = mid;
            }
        }
        
        return nums[left] == target ? left : -1;
    }











