# Graph
- Consists of nodes (vertices) and edges (connections)
- Edges can be directed/undirected or weighted/unweighted
- Ex. Social networks, mapping, recommendations, shortest path

### Representation
Adjacency Matrix
- 2d array (nodes x nodes)
- connections are shown by a 1 or 0
- Ex. index 0 = A, 1 = B: [0][0]: A cycle, [0][1]: A -> B

Adjacency List
- 2d array (node # x edges), hash tables (node key x edges)
- Ex. A index 0: [1, 2] - A is connected to 1 and 2

### Implementation
``` js
class Graph {
	constructor() {
		this.adjacencyList = {};
	}

	// Adds vertex with empty array
	addVertex(vertex) {
		if (!this.adjacencyList[vertex]) this.adjacencyList[vertex] = [];
	}

	// Adds edge between two vertexes
	addEdge(v1, v2) {
		this.adjacencyList[v1].push(v2);
		this.adjacencyList[v2].push(v1);
	}

	// Removes edge of two vertexes
	removeEdge(v1, v2) {
		this.adjacencyList[v1] = this.adjacencyList[v1].filter((v) => v !== v2);
		this.adjacencyList[v2] = this.adjacencyList[v2].filter((v) => v !== v1);
	}

	// Removes vertex and edges of that vertex
	removeVertex(vertex) {
		while (this.adjacencyList[vertex].length) {
			const v = this.adjacencyList[vertex].pop();
			this.removeEdge(vertex, v);
		}
		delete this.adjacencyList[vertex];
	}
}
```

### Traversal Implementation
``` js
	// Depth first search
	dfs(start) {
		let result = [];
		let visited = {};
		let list = this.adjacencyList; // maintain list when this it changes in function

		function traverse(node) {
			// Base case, if node is null
			if (!node) return null;

			visited[node] = true;
			result.push(node);

			// Call on each neighbor
			list[node].forEach((neighbor) => {
				if (!visited[neighbor]) return traverse(neighbor);
			});
		}
		traverse(start);

		// Returns search order
		return result;
	}

	// Breadth first search
	bfs(start) {
		let queue = [start];
		let result = [];
		let visited = {};
		visited[start] = true;

		while (queue.length) {
			let current = queue.pop();
			result.push(current);

			// Visits all neighbors and add to queue to visit its neighbors
			this.adjacencyList[current].forEach((neighbor) => {
				if (!visited[neighbor]) {
					visited[neighbor] = true;
					queue.unshift(neighbor);
				}
			});
		}

		// Returns search order
		return result;
	}
```









