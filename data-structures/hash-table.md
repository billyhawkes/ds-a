---
insertion: 1
removal: 1
searching: n
access: 1
---
# Hash Table
- Used to store human readable key-value pairs, in an unordered manner
- Keys are hashed to a data address, which is used to place the value in memory
- Ex. Python dictionary, Javascript object

### Collisions
When two keys are hashed to the same address
- Seperate Chaining: Stores values at each index in a nested data structure (ex. array)
- Linear Probing: Stores collided value in next empty slot

### Implementation
``` js
// Hashes string to index in length
function hash(key, size) {
	let hash = 31;

	for (let i = 0; i < key.length; i++) {
		hash = (17 * hash * key.charCodeAt(i)) % size;
	}

	return hash;
}

class HashTable {
	constructor() {
		table = new Array(101);
	}

	// Adds a key and value pair to the table
	set(key, value) {
		let index = hash(key, this.table.length);

		// If no items at that index,
		!this.table[index]
			? (this.table[index] = [[key, value]]) // create a new array with the pair,
			: this.table[index].push([key, value]); // otherwise push to existing array
	}

	// Returns value from key
	get(key) {
		let index = hash(key, this.table.length);

		// If items at index
		if (this.table[index]) {
			// Loop through subarray and return value if matching key
			for (let i = 0; i < this.table[index].length; i++) {
				let pair = this.table[index][i];
				if (pair[0] === key) return pair[1];
			}
		}

		// Return undefined if not found
		return undefined;
	}

	// Returns all keys of table
	keys() {
		let keys = [];

		// Loop over table
		for (let i = 0; i < this.table.length; i++) {
			// If table index has any pairs
			if (this.table[i]) {
				// Loop through table index array and push keys
				for (let j = 0; j < this.table[i].length; j++) {
					keys.push(this.table[i][j][0]);
				}
			}
		}

		return keys;
	}

	// Returns all values of table
	values() {
		let values = [];

		// Loop over table
		for (let i = 0; i < this.table.length; i++) {
			// If table index has any pairs
			if (this.table[i]) {
				// Loop through table index array and push values
				for (let j = 0; j < this.table[i].length; j++) {
					values.push(this.table[i][j][1]);
				}
			}
		}

		return values;
	}
}
```