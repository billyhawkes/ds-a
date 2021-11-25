---
insertion: log n
removal: log n
search: n 
---
# Binary Heap
- Each node has at most 2 children 
- No implied ordering between siblings
- Used for priority queues

## Types
- Max Heap: Parent is always larger than children
- Min Heap: Parent is always smaller than children

### Representation
- Using array, any index n:
- left child is 2n + 1
- right child is 2n + 2
- parent is floor((n - 1) / 2)

### Implementation
``` js
class MaxBinaryHeap {
	constructor() {
		values = [];
	}

	swap(i1, i2) {
		let temp = this.values[i1];
		this.values[i1] = this.values[i2];
		this.values[i2] = temp;
	}

	insert(val) {
		// Push to end
		this.values.push(val);

		// Bubble up
		let index = this.values.length - 1;
		let element = this.values[index];
		let parent = Math.floor((index - 1) / 2);

		// While the value of the parent < element and parent != -1 (at start), swap
		while (this.values[parent] < element && parent !== -1) {
			this.swap(index, parent);
			index = parent;
			parent = Math.floor((index - 1) / 2);
		}
	}

	remove() {
		if (this.values.length <= 0) return undefined;

		// Swap with end and pop max
		this.swap(0, this.values.length - 1);
		let max = this.values.pop();

		// Bubble down
		let index = 0;
		let element = this.values[index];
		let length = this.values.length;

		while (true) {
			let left = 2 * index + 1;
			let right = 2 * index + 2;
			let swap = null;

			if (left < length) {
				// If left > right, swap
				if (this.values[left] > element) {
					swap = left;
				}
			}
			if (right < length) {
				// If no swap and right > element or swap exists and right > left, swap with right
				if (
					(swap === null && this.values[right] > element) ||
					(swap !== null && this.values[right] > this.values[swap])
				) {
					swap = right;
				}
			}

			// If no swaps, break
			if (swap === null) break;

			// else, swap and set index to swap
			this.swap(index, swap);
			index = swap;
		}
		return max;
	}
}
```