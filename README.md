# Trip-Planner
A Trip Planner tool coded in DSSL2 for my CS 214 class
POIs refer to Positions Of Interest

Here is an overview of the  Abstract Data Types and Algorithms i Used in this project and my reasoning for them:

------------ADTs---------------
• ADT 1 - Dictionary (HashTable)
Having multiple dictionaries allowed me to have a bidirectional mapping with my graph’s
node IDs and raw xy position, as well as using a dictionary to check for elements in a list
with O(1) time complexity. Additionally, knowing that the names of the Positions of
Interest were unique, I was able to use dictionaries to store each POI by name (key) with
the respective POI struct as its value, which helped me solve the plan_route query.
I chose HashTables because all of its operations are in constant time, making it more
efficient than other Dictionary implementations we learned in this class.


• ADT 2 - WuGraph (Adjacency Matrix)
Using a Weighted Undirected Graph seemed like the obvious choice to represent xy
positions, using the euclidean distance between them as the weights and making it
undirected since you could travel between xy positions freely. Using a graph allowed me
to easily find the n closest things to an xy position and plan a shortest path efficiently.
The Adjacency Matrix seemed like a good choice since the roads had enough connections 
to make the graphs dense enough for our implementation to be space efficient.


• ADT 3 - Priority Queue (Binary Heap)
The use of Priority Queues in my project was small, yet incredibly important. The first
use was within my Dijkstra’s algorithm, where it was used to hold and order which nodes
needed to be worked on in order. The second use was indirectly, when using Heap Sort
to order POI’s closest to a single node for the find_nearby query.Binary Heap is the most efficient implementation of the Priority
Queue ADT (that I learned in class), with remove_min and insert both having O(log(n)) time complexity.


--------------Algorithms--------------
• Algorithm 1 - Dijkstra's
Dijkstra’s algorithm was crucial to solve two of the hardest queries in this project. First,
the preds vector that the algorithm returns was used to find the shortest path from one
node to any other node, which made the plan_route query easier to solve. Second, the
dist vector that the algorithm returns was used in plan_route to sort each POI by its
distance from the start. I wanted to use Breadth First Search on my graph to find the shortest path, but also had
to consider the weights between my nodes, so Dijkstra’s Algorithm was the obvious
choice. This allowed me not only to find the shortest path considering the weights, but
also calculating distances between the nodes.


• Algorithm 2 - Heap Sort
Heap Sort was used within the find_nearby query to sort each node by distance to the
starting location. Once sorted, it was simple to return the n closest. I used heap sort 
because of its good time complexity of O(nlog(n)).
