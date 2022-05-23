# Graph

## Definition

---
A Graph is a non-linear data structure consisting of nodes and edges. The nodes are sometimes also referred to as vertices and the edges are lines or arcs that connect any two nodes in the graph. 

**EXAMPLE:**

For example when we want to reach to area using the Google map we care about the relation between the two node: my current location, and the certain location that i want to go and Google map defines the best way to reach.

![google Map](https://storage.googleapis.com/gweb-cloudblog-publish/images/distances-straight-line.max-2800x2800.max-2200x2200.jpg)

**TERMINOLOGY:**

Here is some common terminology used when working with Graphs:

Vertex - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
Edge - An edge is a connection between two nodes.
Neighbor - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
Degree - The degree of a vertex is the number of edges connected to that vertex.

## Graph types

---

**DIRECTED VS. UNDIRECTED:**

if the relation between two vertices has one direction we called it *Directed Graph*

Unlike an *Undirected Graph*, a Digraph has direction. Each node is directed at another node with a specific requirement of what node should be referenced next.

![Directed Vs. Undirected](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DirectedGraph.PNG)

**Complete vs Connected vs Disconnected:**

- Complete Graphs
A complete graph is when all nodes are connected to all other nodes.
- Connected
A connected graph is graph that has all of vertices/nodes have at least one edge.
- Disconnected
A disconnected graph is a graph where some vertices may not have edges.

<table>
<tr>
<th>Complete Graph</th>
<th>Connected</th>
<th>Disconnected</th>

</tr>
<tr>
<td>

![Image](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/CompleteGraph.PNG)
</td>
<td>

![Image2](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/ConnectedGraph.PNG)
</td>
<td>

![Image](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DisconnectedGraph.PNG)
</td>
</table>

**Acyclic Graph:**

An ***Acyclic Graph*** is a directed graph without cycles.
Cyclic Graphs.  
A ***Cyclic Graph*** is a graph that has cycles. A cycle is defined as a path of a positive length that starts and ends at the same vertex.

## Graph Representation

---

We represent graphs through:

> Adjacency Matrix: is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix

> Adjacency List: is a collection of linked lists or array that lists all of the other vertices that are connected.

**Thinking about how we will implement this in code? Well, let’s look at what the visual is telling us.**

1. We can visually see that we are working with a collection of some sort. The visual is depicting a Linked List, but you could easily make it an array of arrays if you’d like.
2. Each index or node (depending on the data structure you choose to represent the adjacency list) will be a vertex within the graph.
3. Every time you add an edge, you will find the appropriate vertices in the data structure and add it to the appropriate location.

## Weighted Graphs

---

A weighted graph is a graph with numbers assigned to its edges

![weighted](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightGraph.PNG)

When representing a weighted graph in a matrix, you set the element in the 2D array to represent the actual weight between the two paths. If there is not a connection between the two vertices, you can put a 0, although it is known for some people to put the infinity sign instead.

![Weighted matrix](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightMatrix.PNG)

Within adjacency lists, you must include both the weight and the name of the adjacent vertex.

![Adjacency list](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightList.PNG)

## Traversals

---

### 1. Breadth First

**Algorithm:**


**Algorithm:**


1. Enqueue the declared start node into the Queue.
2. Create a loop that will run while the node still has nodes present.
3. Dequeue the first node from the queue
4. if the Dequeue‘d node has unvisited child nodes, add the unvisited children to visited set and insert them into the queue.  

![Breadth](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/BreadthFirst.PNG)

### 2. Depth First

**Algorithm:**

1. Push the root node into the Stack and mark as visited.
2. Start a while loop that runs as long as the stack is not empty.
3. Pop the top node off of the stack and check its neighbors.
4. If a neighbor hasn’t been visited, push it onto the stack and mark as visited.
5. Repeat until the stack is empty.

![Depth](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/Depth1.PNG)

1. Starting by adding our root Node (Node A) to the Stack and marking it as visited.

![1.](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/depthFirst1.png)
2. depending on the order in which Nodes B and D have been added as neighbors

![2](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/depthFirst2.png)
3. We pop off Node B and check its neighbors: Node C, which has not been visited so we add it to the top of the Stack and mark as visited.

![3](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/depthFirst3.png)
4. From here, pop off Node D and check it’s neighbors to add them to our Stack.

![4](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/depthFirst4.png
)

With Node E sitting at the top of the Stack, we pop it off the Stack and check it’s neighbors. There is only one, Node D.
Since Node D has already been visited, we can ignore it and Pop the next node off the Stack: Node H.
We check the neighbors for Node H and notice that both Nodes D and F have previously been visited, so neither are added to the Stack.
Finally we Pop off Node F, and again notice that both neighbors Node D and Node H have already been visited, so we don’t add anything to our Stack.

![5](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/depthFirst5.png)

## Using

---

**Real World Uses of Graphs:**

Graphs are extremely popular when it comes to it’s uses. Here are just a few examples of graphs in use:

GPS and Mapping
Driving Directions
Social Networks
Airline Traffic
Netflix uses graphs for suggestions of products

## Resources

---

1. [CodeFellows](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html)  
2. [GeeksForGeeks](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/)
