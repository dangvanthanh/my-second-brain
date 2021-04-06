Tags: #javascript 

---

# Queue

The queue data structure is a type of First Input First Output (FIFO): the earliest enqueued item is the earlies to dequeue

The queue has main operations: 

- `enqueue`
- `dequeue`

Additionaly, queues can have helper operations like `peek` and `length`


```javascript
class Queue {
	constructor() {
		this.items = {}
		this.headIndex = 0
		this.tailIndex = 0
	}
	
	enqueue(item) {
		this.items[this.tailIndex] = item
		this.tailIndex++
	}
	
	dequeue() {
		const item = this.items[this.headIndex]
		delete this.items[this.headIndex]
		this.headIndex++;
		return item;
	}
	
	peek() {
		return this.items[this.headIndex]
	}
	
	get length() {
		return this.tailIndex - this.headIndex
	}
}
```