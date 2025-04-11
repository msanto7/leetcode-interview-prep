# LeetCode -- 155. Min Stack (Medium)

    - designing a stack with the following 4 operations implemented in constant time
        - push 
        - pop
        - top
        - get min element
    - so I started using a c# list because I thought that would be easy to access and what not
    - I also used a second list to keep track of all of the minimum values in the array...still not sure if that makes complete sense
    - just trying to keep some sort of order
    - but realistically if the minList never contains certians numbers...and all the 'min' values are popped hten this doesn't work
    - so maybe I should just be adding to this list in order and keeping a duplicate copy of all values...which kind of seems dumb but is what it is to get the constant time operations

    - something i didn't originally account for in my thought process was whether or not i would need to deal with invalid operations being called
    - this is something I should definitely be asking at an interview
    - 


# Primtive Solution - (Time: O(n), Space: O(n))

    - here is my first implementation...just using a list of value tuples in c#
    - I am storing the current minimum with each value on the stack and updating as we add items
    - that we we aren't searching for the item or anything to get the min in constant time

    public class MinStack {
        public List<(int, int)> obj;

        public MinStack() {
            obj = new List<(int, int)>();
        }
        
        public void Push(int val) {
            if (obj.Count < 1)
            {
                obj.Add((val, val));
            }
            else
            {
                obj.Add((val, Math.Min(obj[obj.Count - 1].Item2, val)));
            }        
        }
        
        public void Pop() {
            obj.RemoveAt(obj.Count - 1);
        }
        
        public int Top() {
            return obj[obj.Count - 1].Item1;
        }
        
        public int GetMin() {
            return obj[obj.Count - 1].Item2;;
        }
    }