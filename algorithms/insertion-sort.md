---
best: n
average: n^2
worst: n^2
space: 1
---
# Insertion Sort
- Inserts each item into a sorted portion of the array

### Psuedocode
1. Start passes at index 1 as first item is considered sorted
2. Compare item down the sorted left side
3. While the item is less, move each other item up
4. When the item is greater or at the beginning, insert

### Implementation
``` js
function insertionSort(arr) {
	// Start passes at 1 as first element is considered sorted
	for (let i = 1; i < arr.length; i++) {
		let current = arr[i];
		let j = i - 1;
		// Compare item down the sorted left side
		while (j >= 0 && arr[j] > current) {
			// While the item is less, move each other item up
			arr[j + 1] = arr[j];
			j--;
		}
		// When the item is greater or at the beginning, insert
		arr[j + 1] = current;
	}
	return arr;
}
```