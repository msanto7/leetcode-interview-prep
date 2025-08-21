# Leetcode - 153. Find Minimum in Rotated Sorted Array (Medium)

    - alright so we get a rotated sorted array
    - we are returning the minimum element -- the value not the index
    - specifically asks for an o(log(n)) algorithm so already sort of thinking binary search
    - because otherwise we could just can the array and return the first element that is less than the previous i guess
    - but worst case on that is O(n)
    - i still think binary search makes sense...but the reality is because of the pivoting there is no guarantee that the minimum value is to the right or left of the chosen mid value
    - so how can I tweak the idea to work in this case
    - I could do a recursive version that returns the min from both right and left
    - but not sure there really cuts out much time than
    - sike that is constant time...so I should find that point where the decrease happens...

# Primitive Solution - (Time: O(n), Space: O(n))

    - so the first solution that did actually pass surprisingly was a very primitive just search for the first decrease to find the first element

    public int FindMin(int[] nums) {
        // finding the min element
        bool increasing = true;
        int i = 1;

        while (increasing && i <= nums.Length - 1)
        {
            if (nums[i] < nums[i - 1])
            {
                return nums[i];
            }

            i++;
        }

        return nums[0];
    }


# Optimized Solution - (Time: O(log(n)), Space: O(n))

    - so the binary search solution just has one small tweak
    - we pivot on the mid point based on whether or not the mid value is less than the right value...if that is the case than we know that the lowest value is somewhere in the middle so we explore the right side...otherwise we explore the left

    public int FindMin(int[] nums) {
        int left = 0;
        int right = nums.Length - 1;

        while (left < right)
        {
            int mid = left + (right - left) / 2;
            if (nums[mid] > nums[right])
            {
                left = mid + 1;
            }
            else
            {
                right = mid;
            }
        }
        return nums[left];
    }
