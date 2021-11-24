---
insertion: 1
removal: 1
searching: n
access: n
---
# Linked List
- Consists of nodes, where each node has a value and pointer to another node or null
- Contains a head (start), tail (end), and length property
- No indexing / random access

**Singly-linked list**: Each node points to next and last points to null
**Doubly-linked list**: Each node points to next and previous and last nodes next is null
**Circular-linked list**: Each node points to next and last node point to first

### Implementation (Singly)
``` js
class Node {
	constructor(val) {
		this.val = val;
		this.next = null;
	}
}

class SinglyLinkedList {
	// Initializes singly linked list
	constructor() {
		this.tail = null;
		this.head = null;
		this.length = 0;
	}

	// Adds node to the end of the array
	// returns: list
	push(val) {
		// Create a new node with value
		let newNode = new Node(val);

		// If no items, set new node to the head
		if (!this.head) this.head = newNode;
		// Otherwise, set the current tails next to the new node
		else this.tail.next = newNode;

		// Set the new node as tail
		this.tail = newNode;
		// Increment length
		this.length++;
		// Return list
		return this;
	}

	// Removes node from end of the array
	// returns: removed node
	pop() {
		// If empty return undefined
		if (!this.head) return undefined;

		// Traverse the list using a previous and current node until the end
		let previous = this.head;
		let current = this.head;
		while (current.next) {
			previous = current;
			current = current.next;
		}

		// Set tail to previous and previous.next to null
		this.tail = previous;
		previous.next = null;
		// Decrement length
		this.length--;

		// Reset head and tail if no more nodes in list
		if (this.length == 0) {
			this.tail = null;
			this.head = null;
		}

		// Return removed node
		return current;
	}

	// Remove the front node
	// returns: removed node
	shift() {
		// If empty return undefined
		if (!this.head) return undefined;

		// Keep old head and set new head to the next node
		let oldHead = this.head;
		this.head = this.head.next;
		// Decrement length
		this.length--;

		// Set tail to null if list is empty
		if (this.length === 0) this.tail = null;

		// Return removed node
		return oldHead;
	}

	// Adds to beginning of list
	// returns: list
	unshift(val) {
		// Create a new node
		let newNode = new Node(val);

		// If empty list, set the head to the new node
		if (!this.head) this.tail = newNode;
		// Otherwise, set the new nodes next to be the current head
		else newNode.next = this.head;

		// Set new head to the new node
		this.head = newNode;

		// Increment length
		this.length++;

		// Return new node
		return this;
	}

	// Gets value at index
	// returns: node at index
	get(index) {
		// If index out of bounds return undefined
		if (index < 0 || index >= this.length) return undefined;

		// Traverse the list until index
		let current = this.head;
		for (let i = 0; i < index; i++) {
			current = current.next;
		}

		// Return indexed node
		return current;
	}

	// Sets value at a certain index
	// returns: true if success, false if out of bounds
	set(index, val) {
		// Get node at index
		let foundNode = this.get(index);

		// If no node return undefined
		if (!foundNode) return false;

		// Set new value
		foundNode.val = val;

		// Return node
		return true;
	}

	// Inserts new node at index
	// returns: true if success, false if out of bounds
	insert(index, val) {
		// If index out of bounds, return false
		if (index < 0 || index > this.length) return false;

		// If index at the end, push value and return true
		if (index === this.length) return !!this.push(val);
		// If index at the beginning, unshift value and return true
		if (index === 0) return !!this.unshift(val);

		// Create new node
		let newNode = new Node(val);
		// Get Node before index
		let previous = this.get(index - 1);

		// Set new nodes next to previous next
		newNode.next = previous.next;
		// Set previous next to new node
		previous.next = newNode;

		// Increment length
		this.length++;

		// Return true
		return true;
	}

	// Removes item at index
	// returns: removed item
	remove(index) {
		// If index out of bounds, return false
		if (index < 0 || index >= this.length) return undefined;

		// If index at beginning of list, return shift
		if (index === 0) return this.shift();
		// If index at end of list, return pop
		if (index === this.length - 1) return this.pop();

		// Get previous index node
		let previous = this.get(index - 1);
		// Set removed to index node
		let removed = previous.next;
		// Set previous nodes next to removed next
		previous.next = removed.next;

		// Decrement length
		this.length--;

		// Return removed node
		return removed;
	}

	// Reverses list in place
	// returns: reversed list
	reverse() {
		// Swap head and tail
		let current = this.head;
		this.head = this.tail;
		this.tail = node;

		// Set previous and next to null
		let previous = null;
		let next = null;

		// Loop over the list, using previous, node, and next node
		for (let i = 0; i < this.length; i++) {
			// Set next to currents next
			next = current.next;
			// Set currents next node to previous
			current.next = previous;
			// Set previous equal to current
			previous = current;
			// And current equal to next
			current = next;
		}

		// Return list
		return this;
	}
}
```