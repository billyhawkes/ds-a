# Tree
- Consists of nodes in a non-linear parent/child relationship
- Contains a root (top), edges (connection between nodes) and leafs (node with no children)
- Ex. DOM, heirarchy (ex. family, folders, company), AI (Decision tree), etc


## Types
- [binary search tree](binary-search-tree.md)
- [binary heap](binary-heap.md)


## Traversal
### Depth First
- Deep into one path than the next
- Uses Stack

**Pre Order**: visit node, left side, then right side
**Post Order**: visit left, right, then node
**In Order**: visit left, node, then right

### Implementation
``` js
// Pre order
function preDFS(root) {
	let visited = [];

	// node, left, right
	function traverse(node) {
		visited.push(node.value);
		if (node.left) traverse(node.left);
		if (node.right) traverse(node.right);
	}
	traverse(root);

	return visited;
}

// Post order
function postDFS(root) {
	let visited = [];

	// left, right, then node
	function traverse(node) {
		if (node.left) traverse(node.left);
		if (node.right) traverse(node.right);
		visited.push(node.value);
	}
	traverse(root);

	return visited;
}

// In order
function preDFS(root) {
	let visited = [];

	// left, node, right
	function traverse(node) {
		if (node.left) traverse(node.left);
		visited.push(node.value);
		if (node.right) traverse(node.right);
	}
	traverse(root);

	return visited;
}
```


### Breadth First
- Searches level by level
- Uses queue


### Implementation
``` js
// Binary Search Tree Breadth First
function bfs(root) {
	let queue = [root];
	let visited = [];

	// Until queue is finished
	while (queue.length !== 0) {
		// Dequeue
		let current = queue.pop();

		// Enqueue children
		if (current.left) queue.unshift(current.left);
		if (current.right) queue.unshift(current.right);

		// Add current to visited
		visited.push(current.value);
	}

	return visited;
}
```

