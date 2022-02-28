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
# Graph - Add Edge
* remember edge basically means connection

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

    def add_edge(self, v1, v2):
        if v1 in self.adj_list.keys() and v2 in self.adj_list.keys():
            self.adj_list[v1].append(v2)
            self.adj_list[v2].append(v1)
            return True
        return False


my_graph = Graph()

my_graph.add_vertex(1)
my_graph.add_vertex(2)

my_graph.add_edge(1,2)

my_graph.print_graph()
```

***
***
# Graph - Remove Edge
* remember edge basically means connection
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

    def add_edge(self, v1, v2):
        if v1 in self.adj_list.keys() and v2 in self.adj_list.keys():
            self.adj_list[v1].append(v2)
            self.adj_list[v2].append(v1)
            return True
        return False

    def remove_edge(self, v1, v2):
        if v1 in self.adj_list.keys() and v2 in self.adj_list.keys(): 
            try:
                self.adj_list[v1].remove(v2)
                self.adj_list[v2].remove(v1)
            except ValueError:
                pass
            return True
        return False


my_graph = Graph()
my_graph.add_vertex('A')
my_graph.add_vertex('B')
my_graph.add_vertex('C')
my_graph.add_vertex('D')

my_graph.add_edge('A','B')
my_graph.add_edge('B','C')
my_graph.add_edge('C','A')

my_graph.remove_edge('A','D')

my_graph.print_graph()
```


***
***
# Graph - Remove Vertex
* it removes the vertex and all edge connections to it
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

    def add_edge(self, v1, v2):
        if v1 in self.adj_list.keys() and v2 in self.adj_list.keys():
            self.adj_list[v1].append(v2)
            self.adj_list[v2].append(v1)
            return True
        return False

    def remove_edge(self, v1, v2):
        if v1 in self.adj_list.keys() and v2 in self.adj_list.keys(): 
            try:
                self.adj_list[v1].remove(v2)
                self.adj_list[v2].remove(v1)
            except ValueError:
                pass
            return True
        return False

    def remove_vertex(self, vertex):
        if vertex in self.adj_list.keys():
            for other_vertex in self.adj_list[vertex]:
                self.adj_list[other_vertex].remove(vertex)
            del self.adj_list[vertex]
            return True
        return False        


my_graph = Graph()
my_graph.add_vertex('A')
my_graph.add_vertex('B')
my_graph.add_vertex('C')
my_graph.add_vertex('D')

my_graph.add_edge('A','B')
my_graph.add_edge('A','C')
my_graph.add_edge('A','D')
my_graph.add_edge('B','D')
my_graph.add_edge('C','D')

my_graph.remove_vertex('D')

my_graph.print_graph()
```

***
***
# Graph - Review
* Adding a Vertex in a Graph with an Adjacency List is O(1):    
    * True 
* Graphs are the go to data structure when you need to represent entities and the relationships between them:
    * True
* Removing a vertex is O(1):
    * False
    * Finding the vertex is O(1). However, you also have to remove all of the edges associated with the vertex you are removing. 
