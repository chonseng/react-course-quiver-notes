Look at src/playground/es6-let-const.js

# var (not good)
```javascript
var nameVar = "Peter";
var nameVar = 'Mike';
console.log('nameVar', nameVar);
```
Can redefined and reassigned values

# let
Can reassigned
Can't redefined

# const
Can't redefined and reassigned

# Scope
* var is function scope
* let, const are block scope

## var

```jsx
var fullName = "Peter Che";

if (fullName) {
	var firstName = fullName.split(' ')[0];
	console.log(firstName);
}

console.log(firstName); // Works!
```

## let, const

```jsx
var fullName = "Peter Che";

if (fullName) {
	let firstName = fullName.split(' ')[0];
	console.log(firstName);
}

console.log(firstName); // Dont Work!
```

```jsx
/*-------------------
	Solution
-------------------*/
const fullName = "Peter Che";
let firstName;

if (fullName) {
	firstName = fullName.split(' ')[0];
	console.log(firstName);
}

console.log(firstName); // Works!
```

