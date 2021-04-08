Tags: #javascript 

---

# Object Creation Patterns

## Factory Pattern

```javascript
function createPerson(name) {
	const obj = new Object()
	obj.name = name
	obj.showName = function() {
		console.log(`I'm ${object.name}`)
	}
	
	return obj
}

const obsidian = createPerson('Obsidian')
obsidian.showName() // I'm Obsidian
```

## Constructor Pattern

```javascript
function createPerson(name) {
	this.name = name
	this.showName = function() {
		console.log(`I'm ${this.name}`)
	}
}

const obsidian = new createPerson('Obsidian')
obsidian.showName() // I'm Obsidian
```

## Prototype Pattern

```javascript
function Person(name) {
	this.name = name
}

Person.prototype.showName = function() {
	console.log(`I'm ${this.name}`)
}

const obsidian = new Person('Obsidian')
obsidian.showName() // I'm Obsidian
```

## Constructor / Prototype Pattern

```javascript
function Person() {}

Person.prototype.name = '';
Person.prototype.showName = function() {
	console.log(`I'm ${this.name}`)
}

const obsidian = new Person()
obsidian.name = 'Obsidian'
obsidian.showName() // I'm Obsidian
```