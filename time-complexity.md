# Time Complexity
---
## Big O Notation
---
System of comparing code and its performance as input grows
- Worst case upper bound of an algorithm

Determining Big O
- Count up simple operations as c * f(n)
- Drop constants and use highest order
- Ex. O(5n^2 + n) = O(n^2)

###### Time complexities 
- O(1) Constant
	- Arithmitic
	- Assignment
	- Accessing array element (using index)
- O(log n) Logarithmic
- O(n) Linear
	- Ex. For loop
- O(n log n) Linearithmic
- O(n^2) Quadratic
	- Ex. Nested for loops over n
- O(2^n) Exponential
- O(n!) Factorial

###### Space complexities
- O(1)
	- Primitives: numbers, bools, undefined, etc
- O(n)
	- String/Array: where n is the length based on input
	- Objects: where n is the number of keys based on input
	
	
