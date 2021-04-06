Tags: #javascript 

---

# Stack

A stack is a linear data structure that follows a particular order in which the operations are performed. The order is Last In First Out (LIFO)

Stack use `push()` and `pop()` for adding and removing elements respectively.

The following  methods  will be utilized in the stack

- `push()` - adds an element to the stack
- `pop()` - removes and returns  the topmost element of the stack
- `isEmpty()` - returns true or false based on if the stack is empty or not

```javascript
class Stack {
	constructor() {
		this.elements = []
	}
	
	push(element) {
		this.elements.push(element)
	}
	
	pop() {
		if (this.elements.length) {
			return this.elements.pop()
		}
		
		return 'Underflow situation'
	}
	
	isEmpty() {
		if (this.elements.length) {
			return true
		}
		
		return false
	}
}
```


Reversing a string using a stack 

```javascript
function reverse(str) {
	let stack = new Stack()
	let i = 0
	let reversedStr = []
	
	while (i !== str.length) {
		stack.push(str.charAt(i))
		i++
	}
	
	while (!stack.isEmpty()) {
		reversedStr = stack.pop()
	} 
	
	return reversedStr
}
```