# LeetCode -- 328. Odd Even Linked List (Medium)

    - given the head of a linked list as input
    - first node - odd
    - second node - even
    - reorder the list of first all odd nodes and then all even nodes
    - need to retain relative order within the groups

    - so we will obviously be moving around the pointers here...and will likely need to keep maybe 2 pointers 
    - one for curr even and one for curr odd?
    - should be able to do this in one pass through the list
    

# Primtive Solution - (Time: O(n), Space: O(1))

    - fairly intuitive solution just updating pointers to rearrange


    public ListNode OddEvenList(ListNode head) {
        
        if (head == null) { return head; }
        
        ListNode odd = head;
        ListNode even = head.next;
        ListNode firstEven = head.next;

        while (odd != null && odd.next != null && even != null && even.next != null)
        {
            odd.next = even.next;
            odd = even.next;
            even.next = odd.next;
            even = even.next;
        }

        odd.next = firstEven;

        return head;
    }















