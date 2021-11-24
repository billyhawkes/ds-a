---
best: 1
average: n
worst: n
space: 1
---
# Linear Search
- Search every item one at a time in order 
- Used on unsorted data

### Implementation
``` js
function linearSearch(arr, val) {
	// Loops through array
	for (let i = 0; i < arr.length; i++) {
		// Return index if value matches
		if (arr[i] === val) {
			return i;
		}
	}
	// Return -1 if no value was found
	return -1;
}
```