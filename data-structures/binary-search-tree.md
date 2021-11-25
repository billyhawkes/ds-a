---
insertion: log n
searching: log n
# Based on levels 
---
# Binary Search Tree
- Each node has at most 2 children
- Left child: lesser than node
- Right child: greater than node

### Implementation
``` js
class Node {
	constructor(value) {
		this.value = value;
		this.left = null;
		this.right = null;
	}
}

class BinarySearchTree {
	constructor() {
		this.root = null;
	}

	// Inserts value into BST
	insert(value) {
		// Create new Node
		let newNode = new Node(value);

		// If no root (empty bst), set new node as root
		if (!this.root) {
			this.root = newNode;
			return this;
		}

		let current = this.root;
		while (true) {
			// If duplicate, return undefined (can also set count on nodes)
			if (newNode.value === current.value) return undefined;
			// If new node > current, put new node as right or move to existing right
			if (newNode.value > current.value) {
				if (!current.right) {
					current.right = newNode;
					return this;
				} else current = current.right;
			}
			// If new node < current, put new node as left or move to existing left
			else if (newNode.value < current.value) {
				if (!current.left) {
					current.left = newNode;
					return this;
				} else current = current.left;
			}
		}
	}

	// Searches for value
	contains(value) {
		// If no root return false
		if (!this.root) return false;

		let current = this.root;
		while (true) {
			// If value equals current, return true
			if (value === current.value) return true;
			// If value > current, move to right, if empty return false
			if (value > current.value) {
				if (current.right) current = current.right;
				else return false;
			}
			// If value < current, move to left, if empty return false
			if (value < current.value) {
				if (current.left) current = current.left;
				else return false;
			}
		}
	}

	// Search recursively
	containsRecursive(value, root = this.root) {
		// Base case if root is null
		if (root === null) return false;

		// If value equals root, return true
		if (value === root.value) return true;
		// If value > root, recall with right child as root
		else if (value > root.value)
			return this.containsRecursive(value, root.right);
		// If value < root, recall with left child as root
		else if (value < root.value)
			return this.containsRecursive(value, root.left);
	}
}
```
