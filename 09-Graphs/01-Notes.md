# Graphs
***
***
# Graph Intro
* vertex / node
* between the verticies you have whats called an "edge or connection"
* there is no limit to how many other vertacies a vertex can connect to
* with graphs you can have weighted edges (think BGP - shortest path)
* you can have bi-directional or directional edges
* trees are a form of graphs but they have limitations
    * a linked list is also a form of a graph

***
***
# Graph - Adjacency Matrix
* you can represent a graph as an adjacency matrix or an adjacency list
* look at the image below - a has edges with b and e so its has 1's
* left axis is the actual vertex
* top axis is what edges the vertex connects to
* ![](../images/graph-am.png)
* if you change the b section you can change it from bi-directional to only directional:
* ![](../images/graph-directional.png)
* if you want the routes to be weighted then instead of using ones you can use different numbers (to show the weight)

***
***
# Graph - Adjacency List
* an adjacency list is a way that you can represent the graph 
* you can represent it as a dictionary
```
{
    'A':['B','E'],
    'B':['A','C'],
    'C':['B','D'],
    'D':['C','E'],
    'E':['A','D'],
}
```

***
***
# Graph - Big O
* in an adjacency matrix you have to store all of the verticies you are connected to but also all of the vertacies it is NOT connected to
  * so its O( |V|^2 )
  * V is verticies
  * adding new items or a new collum is much more complex
  * to append its O( |V|^2 )
  * to add an edge its O(1)
  * to remove an edge: O(1)
  * remove a vertex: O( |V|^2 )
* in an adjacency list it only stores the verticies that it is connected to
  * so its O( |V|+|E| ) 
  * V is verticies
  * E is edges
  * to append its O(1)
  * to add an edge its O(1)
  * to remove an edge: O(|E|)  (number of edges)
  * remove a vertex: O( |V|+|E| )
  * adjacency lists are typically more simple and more efficent

***
***
# Graph - Add Vertext
* aka add a node (which is a vertex)
```
class Graph:
    def __init__(self):
        self.adj_list = {}

    def print_graph(self):
        for vertex in self.adj_list:
            print(vertex, ':', self.adj_list[vertex])

    def add_vertex(self, vertex):
        if vertex not in self.adj_list.keys():
            self.adj_list[vertex] = []
            return True
        return False


my_graph = Graph()

my_graph.add_vertex('A')

my_graph.print_graph()
```

***
***
# 