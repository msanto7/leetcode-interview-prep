# LeetCode -- 206. Reverse Linked List (Easy)

    - input is the head of a single linked list
    - need to return the list in reverse
    - so I am assuming this is going to again be a pretty intuitive pointer updating solution
    - could also create a new linked list while iterating through this one potentially
    - but not sure at the moment how to due it in O(1) space
    
    - there is also a recursive solution here as well...but might table that for now..it also bumps the space complexity to O(n)

# Primtive Solution - (Time: O(n), Space: O(1))

    - so pretty straight forward pointer updates...single pass with 3 extra nodes used to keep track and swap pointers
    - because i started with cur and prev pointers at the same head node...I made this logic slightly more complicated than it needs to be
    - solution has no conditional logic in the while loop if i just start the prev and curr pointers 1 node apart


    public ListNode ReverseList(ListNode head) {
        ListNode prev = head;
        ListNode curr = head;
        ListNode temp = null;

        while (curr != null)
        {
            if (prev == curr)
            { 
                temp = curr.next;
                curr.next = null;
                curr = temp;
            }
            else
            {
                temp = curr.next;
                curr.next = prev;
                prev = curr;
                curr = temp;
            }
        }

        head = prev;
        return head;
    }










