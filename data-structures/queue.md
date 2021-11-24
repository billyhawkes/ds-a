---
insertion: 1
removal: 1
searching: n
access: n
---
# Queue
- FIFO: First In First Out
- Ex. Waiting in line, game lobby queue, computer downloads, etc

### Implementation (Array)
``` js
let queue = []

// First pair
queue.push(1) // Add to end (enqueue)
queue.shift() // Remove from beginning (dequeue)

// Second pair
queue.unshift(1) // Add to beginning (enqueue)
queue.pop() // Remove from end (dequeue)

```