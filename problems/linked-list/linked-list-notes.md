# Linked List

    - nodes linked together using pointers
    - single and double linked lists
    - pointers allow non-contiguous storage for this data structure

# C#

    https://www.geeksforgeeks.org/linked-list-implementation-in-c-sharp/ 
    https://www.geeksforgeeks.org/c-sharp-linkedlist-class/

    LinkedList<int> l = new LinkedList<int>();

## When to use

    Use Case: Stacks, Queues, LRU Cache, Dynamic Data Manipulation
    Why? LinkedList<T> allows O(1) insertions/deletions at the head, tail, or middle if you have the node reference.

    Use Case	                                    Best Data Structure	           Why?
    Frequent insertions/deletions at head/tail	    LinkedList<T>	               O(1) insertion/removal
    Need a stack	                                LinkedList<T>	               Works like a stack but allows O(1) middle removal
    Need a queue/deque	                            LinkedList<T>	               Supports O(1) insertion/removal at both ends
    Need a circular buffer	                        LinkedList<T>	               Easily implements circular structures


    ✅ Key Methods in LinkedList<T>

    Method	                        Description
    AddFirst(value)	                Adds an element at the beginning
    AddLast(value)	                Adds an element at the end
    AddBefore(node, value)	        Inserts before a given node
    AddAfter(node, value)	        Inserts after a given node
    Find(value)	                    Finds a node with a specific value
    Remove(value)	                Removes a node by value
    RemoveFirst()	                Removes the first node
    RemoveLast()	                Removes the last node


     When NOT to Use Linked Lists
        ❌ If you need random access (O(1)) → Use List<T> instead.
        ❌ If you are just appending elements at the end → Use List<T> or Queue<T>.
        ❌ If you care about memory overhead → LinkedList<T> requires extra storage for pointers.