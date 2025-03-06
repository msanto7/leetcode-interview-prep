# Queue

    - First In First Out (FIFO) data structure
    - 

    Operation	            Method (C#)	            Time Complexity
    Enqueue (Push)	        queue.Enqueue(x);	    O(1)
    Dequeue (Pop)	        queue.Dequeue();	    O(1)
    Peek (Front Element)	queue.Peek();	        O(1)
    Check Empty	            queue.Count == 0;	    O(1)



# C#

    --> https://www.geeksforgeeks.org/c-sharp-queue-class/ 

    using System;
    using System.Collections.Generic;

    class Program {
        static void Main() {
            Queue<int> queue = new Queue<int>();

            // Enqueue elements
            queue.Enqueue(1);
            queue.Enqueue(2);
            queue.Enqueue(3);

            Console.WriteLine(queue.Peek()); // Output: 1 (Front element)

            // Dequeue elements
            Console.WriteLine(queue.Dequeue()); // Output: 1
            Console.WriteLine(queue.Dequeue()); // Output: 2

            Console.WriteLine(queue.Count); // Output: 1
        }
    }



## When to use

    ✅ Breadth-First Search (BFS) → Used in graphs & trees
    ✅ Level-order traversal → Tree problems
    ✅ Sliding Window Problems → Use Deque (Double-ended queue)
    ✅ Task Scheduling & Order Processing → Simulate execution order
    ✅ Shortest Path Problems → Unweighted graph traversal