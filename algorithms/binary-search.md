# Binary Search
- Divide and conquer based on middle item value
- Used on sorted arrays
- Ex. Looking in a dictionary

### Implementation
``` js
function binarySearch(arr, val) {
	let left = 0;
	let right = arr.length - 1;

	while (left <= right) {
		// Calculate middle
		let middle = Math.floor((left + right) / 2);

		// If middle equals val, return
		if (arr[middle] === val) return middle;
		// If val is greater or less than middle, shift middle
		else if (val > arr[middle]) left = middle + 1;
		else if (val < arr[middle]) right = middle - 1;
	}

	// Return -1 if no value found
	return -1;
}
```