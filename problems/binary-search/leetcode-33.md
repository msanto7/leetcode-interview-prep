# Leetcode - 33. Search in Rotated Sorted Array (Medium)

    - another pivoted sorted array
    - so now we are searching for the index of a specific targeted integer value
    - if the target is not in the array just return -1
    - so I can still use the same logic i suppose of fining the mid...and if the value at mid is greater than the value of the right side...

# Primitive Solution - (Time: O(n), Space: O(n))

    - this was my first try still failing one of the cases right now
    - I am skipping over the target value with my current logic...I need to handle the left side better somehow...I also feel like the pivot is off
    - just needed a few tweaks in the logic to get this working
    - but following the same idea of using the binary search with the context of the pivot being in one of the sides to determine where our search item is

    public int Search(int[] nums, int target) {
        int left = 0;
        int right = nums.Length - 1;

        while (left < right)
        {
            var mid = left + (right - left) / 2;
            if (nums[mid] == target) { return mid; }
            if (nums[left] == target) { return left; }
            if (nums[right] == target) { return right; }
            if ((nums[mid] > nums[right] && ((target < nums[mid]) && (target < nums[right]) || target > nums[mid]))
                ||
                (nums[mid] <= nums[right] && (target > nums[mid]) && (target < nums[right]))
                )
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











