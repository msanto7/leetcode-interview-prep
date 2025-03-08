# LeetCode -- 2095. Delete the Middle Node of a Linked List (Medium)

    - head node is the input
    - we are returning the head of the modified linked list
    - need to determine what the middle node is and delete it
    - need to take into account even and odd length lists
    - we are given the definiton of a middle node being the floor of n / 2
    - we are also given a specific linkedList class definition that does not contain a count...so wondering if we need to traverse to find the count
    
    - in general the delete process should look like this
    - if we have node A, B and C
    - and we are deleting node B...we need to take the pointer of node A (next) and move it to the current next pointer of node B
    - and that should be it...it leaves node B hanging

    - so I am going to traverse to get the count of nodes to start
    - 
    

# Primtive Solution - (Time: O(n), Space: O(1))

    - this was my first stab at a solution...i have to go atleast all the way through and another half way through the list
    - not sure if there is much of an optimization


    public ListNode DeleteMiddle(ListNode head) {

        ListNode curr = head;
        int n = 1;

        if (head.next == null) { return null; }

        // determine node count
        while (curr.next != null)
        {
            curr = curr.next;
            n++;
        }

        var mid = n / 2;
        curr = head;
        ListNode prev = new ListNode();

        for (int i = 0; i <= mid; i++)
        {
            // save the previous pointer
            if (i == mid - 1)
            {
                prev = curr;
            }

            if (i == mid)
            {
                prev.next = curr.next;
            }

            curr = curr.next;
        }

        return head;
    }



# Optimized Solution - (Time: O(n), Space: O(1))

    - so a fast and slow pointer can be used to only traverse the linked list once while figuring out the middle element














