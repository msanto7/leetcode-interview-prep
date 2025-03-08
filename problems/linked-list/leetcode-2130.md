# LeetCode -- 2130. Maximum Twin Sum of a Linked List (Medium)

    - head of linked list is the input
    - number of nodes is even
    - twin is defined as the ith node -- and the (n-1-i)th
    - so we want the maximum twin sum
    - and I guess the main issue here is that we have to continually traverse through the linked list to get the twin nodes even though we know the index
    - ...so...
    - maybe there is another sort of fast slow pointer way of getting through this
    - sort of a head and tail, right and left pointer situation...so we have to traverse all the way through to get the initial state
    - then we are moving each point by 1 after that...although moving from right to left is going to be difficult with the right side pointer
    - so I don't reall think that solves the problem exactly
    - 



# Optomized Solution - (Time: O(n), Space: O(1))

    - alright so this is my first solution figuring out the middle node using 2 pointers...then reversing the second half of the list
    - then just comparing those 2 halfs adding index for index and taking the greatest value...
    - seems a bit simple and primitive but i overall not that inefficient
    - and after looking at the editorial it is actually the only proposed solution that doesn't just use another type of datastructure to store the list and make it easier
    - so this solution makes sense...it would maybe just be hard to come up with reversing the second half on the spot


    public int PairSum(ListNode head) {

        ListNode slow = head;
        ListNode fast = head;
        ListNode prev = head;
        int maxSum = 0;

        if (head.next.next == null) { return head.val + head.next.val; }

        while (fast != null)
        {
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
        }

        // slow is now half way through the linked list...so we could reverse this portion now
        prev.next = null;
        fast = slow.next;
        slow.next = null;
        while (fast != null)
        {
            prev = fast.next;
            fast.next = slow;
            slow = fast;
            fast = prev;
        }

        prev = head;

        // now traverse thru both and do the addition
        while (prev != null && slow != null)
        {
            if (slow.val + prev.val > maxSum) { maxSum = slow.val + prev.val; }

            prev = prev.next;
            slow = slow.next;
        }
        
        return maxSum;
    }






