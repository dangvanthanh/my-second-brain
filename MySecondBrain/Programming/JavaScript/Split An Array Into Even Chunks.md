Tags: #javascript 

---

# Split An Array Into Even Chunks

In example, we have an array `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]` and we want to chunks by size such as

```javascript
// Chunk by 3
[ [1, 2, 3], [4, 5, 6], [7, 8, 9], 10 ]

// Or chunk by 2
[ [1, 2], [3, 4], [5, 6], [7, 8], [9, 10] ]
```

We'll take a look at 2 approaches

- Using `slice()` method and `for` loop
- Using `splice()` method and `while` loop

## Use `slice()` method

```javascript
function sliceIntoChunk(arr, chunkSize) {
	let result = []
	
	for (let i = 0; i < arr.length; i += chunkSize) {
		const chunk = arr.slice(i, i + chunkSize)
		result.push(chunk)
	}
	
	return result
}
```

## Use `splice()` method

```javascript
function spliceIntoChunk(arr, chunkSize) {
	let result = []
	
	while (arr.length) {
		const chunk = arr.splice(0, chunkSize)
		result.push(chunk)
	}
	
	return result
}
```