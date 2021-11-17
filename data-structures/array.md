---
Insertion: depends...
Removal: depends...
Access: O(1)
Searching: O(n)
---
# Array
---
- Indexible continuous chunk of memory
- Fixed length of a single type
- Adding element to end, language creates a new array with a longer length and copies the origional

Insertion
- End: O(1)
- Beginning: O(n), must change all indices

Removal
- End: O(1)
- Beginning: O(n), must change all indices

###### Use Case
- When you need order 
	- Use an object (hash map) if order doesn't matter