---
best: n log n
average: n log n
worst: n^2
# n decompositions (already sorted), n comparisions
space: log n
---
# Quick Sort
- Selects a pivot item and moves smaller items to left and bigger to right

### Implementation
``` js
function quickSort(arr, left = 0, right = arr.length - 1) {
	if (left < right) {
		// Calls pivot on the array
		let pivotIndex = pivot(arr, left, right);

		// Recursively calls quick sort on left and right sides
		quickSort(arr, left, pivotIndex - 1);
		quickSort(arr, pivotIndex + 1, right);
	}
	// When subarray (left to right) is 1 or less items return
	return arr;
}

function pivot(arr, start = 0, end = arr.length + 1) {
	// Pick pivot and store pivot index
	let pivot = arr[start];
	let pivotIndex = start;

	// Loop through array
	for (let i = start + 1; i <= end; i++) {
		// If item is less than pivot, add to pivot index, and swap item
		if (arr[i] < pivot) {
			pivotIndex++;
			let temp = arr[i];
			arr[i] = arr[pivotIndex];
			arr[pivotIndex] = temp;
		}
	}

	// Swap pivot with pivot index
	arr[start] = arr[pivotIndex];
	arr[pivotIndex] = pivot;

	return pivotIndex;
}
```