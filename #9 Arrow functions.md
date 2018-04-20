src/playground/es6-arrow

Anonymous

```jsx
const squareArrow = (x) => {
	return x * x;
}

```

```jsx
//OR
const squareArrow = (x) => x * x;
```

```jsx
const times = (x, y) => {
	return x * y;
}
```

Part 2
======

Arguments object - no longer bound with arrow function
------------------------------------------------------

If we want to access the arguments object, we need to stick to the ES5 function.

```jsx
/*-------------------
	Working
-------------------*/
const add = function(a, b) {
	console.log(arguments); // Works
	return a + b;
}
console.log(add(55, 1, 101));

/*-------------------
	Not working
-------------------*/
const add = (a, b) => {
	console.log(arguments); // arguments can't be accessed
	return a + b;
}
console.log(add(55, 1, 101));
```

```jsx
// this keyword - no longer bound in Arrow fctn

/*-------------------
	Doesn't work
-------------------*/
const user = {
	name: 'Peter',
	cities: ['Philadelphia', 'New York', 'Dublin'],
	printPlacesLived: function() {
		// function will bound the this to its own
		this.cities.forEach(function (city) {
			console.log(this.name + ' has lived in ' + city);
			// Errors: this is not defined
		})
	}
}
user.printPlacesLived();

/*-------------------
	Works
-------------------*/
const user = {
	name: 'Peter',
	cities: ['Philadelphia', 'New York', 'Dublin'],
	printPlacesLived: function() {
		// Arrow function doesn't bound it's own this
		this.cities.forEach((city) => {
			console.log(this.name + ' has lived in ' + city);
		})
	}
}
user.printPlacesLived();
```

ES6

```jsx
const user = {
	printPlacesLived() {
		this.cities.forEach((city) => {
			console.log(this.name + ' has lived in ' + city);
		})
	}
}
```



