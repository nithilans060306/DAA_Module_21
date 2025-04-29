# EX 3B Hamiltonian Circuit Problem
## DATE: 12/04/2025
## AIM: To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm:

1. **Initialize Graph and Path**
   - Create an adjacency matrix `graph` of size `V × V` (where `V` is number of vertices).
   - Initialize a `path` list of size `V` with `-1` to track the current path of vertices.

2. **Start from First Vertex**
   - Set the first vertex of the path as 0 (starting point of the cycle).

3. **Backtracking Utility Function (`hamCycleUtil`)**
   - If `pos == V`, check if there's an edge from the last vertex in the path back to the first vertex to complete the cycle.
   - For each vertex `v` from 1 to `V-1`:
     - Check if it is **safe** to add `v` to the path:
       - It must be adjacent to the last vertex added.
       - It must not already be in the path.
     - If safe, add it to `path[pos]` and recursively call `hamCycleUtil` with `pos + 1`.
     - If recursion returns False, backtrack by setting `path[pos] = -1`.

4. **Safety Check Function (`isSafe`)**
   - Return `False` if:
     - There is no edge between the previous vertex and current.
     - The vertex already exists in the path.
   - Otherwise, return `True`.

5. **Main Function (`hamCycle`)**
   - Initialize path and call the utility function.
   - If a valid Hamiltonian cycle is found, print the path.
   - If not, print that no solution exists.
  

## Program:
```python
/*
Program to implement to check whether Hamiltonian path exits in the given graph.
Developed by: Nithilan S
Register Number: 212223240108
*/
class Graph():
    def __init__(self, vertices):
        self.graph = [[0 for column in range(vertices)]
                            for row in range(vertices)]
        self.V = vertices
    def isSafe(self, v, pos, path):
        if self.graph[ path[pos-1] ][v] == 0:
            return False
        for vertex in path:
            if vertex == v:
                return False
 
        return True
    def hamCycleUtil(self, path, pos):
        ######################Add your code here#################################
        if pos == self.V:
            if self.graph[path[pos-1]][path[0]] == 1:
                return True
            else:
                return False

        for v in range(1, self.V):
            if self.isSafe(v, pos, path):
                path[pos] = v
                if self.hamCycleUtil(path, pos + 1):
                    return True
                path[pos] = -1
        return False
        
 
    def hamCycle(self):
        path = [-1] * self.V
        path[0] = 0
 
        if self.hamCycleUtil(path,1) == False:
            print ("Solution does not exist\n")
            return False
 
        self.printSolution(path)
        return True
 
    def printSolution(self, path):
        print ("Solution Exists: Following",
                 "is one Hamiltonian Cycle")
        for vertex in path:
            print (vertex, end = " ")
        print (path[0], "\n")
g1 = Graph(5)
g1.graph = [ [0, 1, 0, 1, 0], [1, 0, 1, 1, 1],
            [0, 1, 0, 0, 1,],[1, 1, 0, 0, 1],
            [0, 1, 1, 1, 0], ]
g1.hamCycle();
```

## Output:
![image](https://github.com/user-attachments/assets/7b5c0dd6-d1d2-4c24-80fa-617860ecd055)



## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
