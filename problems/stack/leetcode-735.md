# LeetCode -- 735. Asteroid Collision (Medium)

    - single int array input...returning an integer array
    - indices represent relative position
    - absolute value represents its size...and the sign represents its direction
    - positive = right, negative = left
    - if 2 asteroids meet...the smaller one will explode
    - if same size, both will explode
    - same direction will never meet
    
    - so without looking at examples yet, it sounds like we need to loop through the array and do the math on the collisions
    - and return the array after all exploded asteroids are removed
    
    - so the look back should happen when we switch signs 
    - so yea I think just iterating...pushing on the stack...popping and comparing size when we switch signs...and the pushing the winner...
    - then convert the remaining stack values to an array

    - ** this is mentioned in the question constraints...but something I would want to ask here is how to handle 0 in the array


    - so I wrote up a solution matching the above...but what i didn't take into account is that from left to right
    - if an asteroid is moving to the left (negative) and is to the left of an asteroid moving to the right..they wont collide
    - also once we pop and compare values...whichever values wins has to be compared to the next pop to make sure it is alright
    - so I need another looping strucure nested in unfortunately
    - the problem is though each time i look back into the stack...I need to figure out if there is a sign change...and what direction it is in




# Primtive Solution - (Time: O(n), Space: O(n))

    - so I came up with a solution after a lot of failed runs and debugging
    - there has to be a better way to go about this process...although i think it is relatively efficient idk


    public int[] AsteroidCollision(int[] asteroids) {
        Stack<int> space = new Stack<int>();
        var pos = asteroids[0] > 0 ? true : false;
        space.Push(asteroids[0]);

        for (int i = 1; i < asteroids.Length; i++)
        {
            // sign hasn't changed
            if (pos && asteroids[i] > 0 || !pos)
            {
                space.Push(asteroids[i]);
            }
            else
            {
                var winner = asteroids[i];
                var both = false;

                // recompare with the remaining stack
                while (space.Count() > 0)
                {
                    // sign has changed...pop...compare...push
                    var last = space.Pop();             
                    if (Math.Abs(last) > Math.Abs(asteroids[i]) && last > 0 && winner < 0) { winner = last; }
                    else if (Math.Abs(last) < Math.Abs(asteroids[i]) && last > 0 && winner < 0) { winner = asteroids[i]; }
                    // if same size..don't push either...both explode
                    else if (last > 0 && winner > 0 || last < 0 && winner < 0 || last < 0 && winner > 0)
                    {
                        space.Push(last);
                        space.Push(winner);
                        both = true;
                        break;
                    }
                    else { both = true; break; }
                }

                if (!both) { space.Push(winner); }    
            }

            pos = space.Count() > 0 && space.Peek() > 0 ? true : false;
        }

        return space.Reverse().ToArray();
    }