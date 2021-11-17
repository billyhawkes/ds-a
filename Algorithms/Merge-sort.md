---
best: n log n
average: n log n
worst: n log n
# log n decompositions, n comparisons
space: n
---
# Merge sort
---
- Divide and conquer
- Works by splitting array into smaller arrays of length 0 or 1, then merging to build a new sorted array

###### Merge sort Pseudocode
1. Call mergeSort on left and right half until you have arrays of 0 or 1 items
2. Merge the left and right arrays until you are back to full length
3. Base: if array has 1 or less items

###### Merge sort Implementation
``` js
function mergeSort(arr) {
	if (arr.length <= 1) {
		return arr;
	}
	let mid = Math.floor(arr.length / 2);

	// Call mergeSort on left and right half until you have arrays of 0 or 1 items
	let left = mergeSort(arr.slice(0, mid));
	let right = mergeSort(arr.slice(mid));

	// Merge the left and right until you are back to full length
	return merge(left, right);
}
```

###### Merge Pseudocode
1. Create empty array
2. While there are still values to compare
	1. If the value in first < second, push first and move to next item in first array
	2. Else, second < first (or equal), push the second and move to next item in second array
	3. Once you finish one array, push all the values of the other

###### Implementation
``` js
function merge(arr1, arr2) {
	// Create empty array
	let result = [];

	let first = 0;
	let second = 0;

	// While there are still values to compare
	while (first < arr1.length && second < arr2.length) {
		// if first < second, push first and move to next item in first array
		if (arr1[first] < arr2[second]) {
			result.push(arr1[first]);
			first++;
		} 
		// Else, if second < first (or equal), push the second and move to next item in second array
		else {
			result.push(arr2[second]);
			second++;
		}
	}
	
	// Push all the extra values
	while (first < arr1.length) {
		result.push(arr1[first]);
		first++;
	}
	while (second < arr2.length) {
		result.push(arr2[second]);
		second++;
	}

	return result;
}
```
