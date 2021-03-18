Tags: #javascript 

---

# Navigator Clipboard API

```javascript
// Write to clipboard
document.addEventListerner('click', async (e) =>
	await navigator.clipboard.writeText('Clipboard')
)

// Read from clipboard
document.addEventListerner('click', async (e) => {
	const text = await navigator.clipboard.readText()
	console.log(text);
})
```