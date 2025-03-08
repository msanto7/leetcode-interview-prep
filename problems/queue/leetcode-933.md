# LeetCode -- 933. Number of Recent Calls (Easy)

    - alright so it makes sense to create a queue of requests...storing the integer time of the request in each
    - and i guess 





    

# Primtive Solution - (Time: O(n), Space: O(n))

    - this solution uses a queue to store the requests and there times...traverses the queue like a sliding window almost to keep it storing within the last 3000 milliseconds
    

    public class RecentCounter {

        public Queue<int> recentRequests;

        public RecentCounter() {
            recentRequests = new Queue<int>();
        }
        
        public int Ping(int t) {
            recentRequests.Enqueue(t);
            // t is the time of the request

            while (recentRequests.Count > 0 && (t - recentRequests.Peek()) > 3000)
            {
                recentRequests.Dequeue();
            }
            
            return recentRequests.Count;
        }
    }









