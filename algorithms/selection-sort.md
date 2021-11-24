---
best: n^2
average: n^2
worst: n^2
space: 1
---
# Selection sort
- Selects smallest value and places at the beginning
- After each pass, the first value is sorted

### Implementation
``` js
function selectionSort(arr) {
	//  Passes over the array
	for (let i = 0; i < arr.length; i++) {
		// Store first element as the current min
		let min = i;
		// Loop through unsorted items to find min
		for (let j = i + 1; j < arr.length; j++) {
			// Set item to min if its lower than current min
			if (arr[j] < arr[min]) {
				min = j;
			}
		}
		// If min isn't already at the start, swap
		if (min !== i) {
			let temp = arr[min];
			arr[min] = arr[i];
			arr[i] = temp;
		}
	}
	return arr;
}
```