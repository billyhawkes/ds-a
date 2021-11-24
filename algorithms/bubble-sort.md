---
best: n
average: n^2
worst: n^2
space: 1
---
# Bubble Sort
- Compares each item to the next and swaps if out of order
- "Bubbles" the items up
- After each pass, the last value is sorted

### Implementation
``` js
function bubbleSort(arr) {
	// Outer loop (passes)
	for (let i = arr.length; i > 0; i--) {
		let swap = false;
		// Inner loop (through array)
		for (let j = 0; j < i - 1; j++) {
			// Swap if arr[j] is greater than arr[j+1]
			if (arr[j] > arr[j + 1]) {
				let temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
				swap = true;
			}
		}
		// If no swaps break out of loop
		if (!swap) break;
	}
	return arr;
}
```