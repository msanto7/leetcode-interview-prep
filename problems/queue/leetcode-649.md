# LeetCode -- 649. Dota2 Senate (Medium)

    - round based procedure
    - each round a senator can either 
        - ban 1 senators right (for this and all following rounds)
        - announce the victory
    - length of string is the num of senators
    - the output is the string of either of the 2 parties
    - this wasn't as explicitly said...but it sounds like the length of the string is also the number of rounds based on the examples
    - just kidding it sounds like it goes until a decision can be made so no set amount of rounds

    - so we are obviously supposed to use a queue to solve this somehow...lets think about some ways this might work
    - maybe the queue handles who is actively in the voting still
    - pop when a senator has been revoked of rights
    - so order of the senators matters...but it almost comes down to who has the most senators still
    - could use a queue for each party type maybe...and pop until empty


    questions
        - can the senator that is banning another senators rights pick anyone...or is it just the next senator in line??
    
    - so announcing victory is the only way to end the voting??
    - 

# Double Queue Solution - (Time: O(n), Space: O(n))

    - so there are a number of different solutions here...this is one using 2 queue which is most similar to what I starte out doing
    - it is based on the fact that the order of each senator matters and first bans next


    public string PredictPartyVictory(string senate) {
        Queue<int> rad = new Queue<int>();
        Queue<int> dir = new Queue<int>();
        int n = senate.Length;

        for (int i = 0; i < n; i++)
        {
            if (senate[i] == 'R')
            {
                rad.Enqueue(i);
            }
            else
            {
                dir.Enqueue(i);
            }
        }
        
        while (rad.Count > 0 && dir.Count > 0)
        {
            int r = rad.Dequeue();
            int d = dir.Dequeue();

            if (r > d)
            {
                dir.Enqueue(r + n);
            }
            else
            {
                rad.Enqueue(d + n);
            }
        }

        return rad.Count == 0 ? "Dire" : "Radiant";
    }


# Single Queue Solution - (Time: O(n), Space: O(n))









