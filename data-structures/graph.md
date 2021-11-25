# Graph
- Consists of nodes (vertices) and edges (connections)
- Edges can be directed/undirected or weighted/unweighted
- Ex. Social networks, mapping, recommendations 

### Representation
Adjacency Matrix
- 2d array (nodes x nodes)
- connections are shown by a 1 or 0
- Ex. index 0 = A, 1 = B: [0][0]: A cycle, [0][1]: A -> B

Adjacency List
- 2d array (node # x edges), hash tables (node key x edges)
- Ex. A index 0: [1, 2] - A is connected to 1 and 2

## Traversal