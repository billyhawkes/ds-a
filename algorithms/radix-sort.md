---
# k - number of digits
best: nk
average: nk
worst: nk
space: n + k
---
# Radix Sort
- Does not make comparisons and works on numbers
- Groups based on digits for each digit from the end to beginning

### Implementation
``` js 
function radixSort(arr) {
	// Finds max amount of digits
	let digits = mostDigits(arr);

	// Loops through number of digits
	for (let i = 0; i < digits; i++) {
		// Creates array to store number buckets
		let buckets = [[], [], [], [], [], [], [], [], [], []];

		// Places each number based on its corresponding kth element
		for (let j = 0; j < arr.length; j++) {
			buckets[getDigit(arr[j], i)].push(arr[j]);
		}

		// Replace existing array with values in each bucket (0-9)
		arr = [].concat(...buckets);
	}
	return arr;
}

// Gets digit at position
function getDigit(num, place) {
	return Math.floor((Math.abs(num) / Math.pow(10, place)) % 10);
}

// Counts the number of digits
function digitCount(num) {
	if (num === 0) return 1;
	return Math.floor(Math.log10(Math.abs(num))) + 1;
}

// Finds max digits in an array
function mostDigits(arr) {
	let most = 0;
	for (let num of arr) {
		let digits = digitCount(num);
		if (digits > most) most = digits;
	}
	return most;
}
```
