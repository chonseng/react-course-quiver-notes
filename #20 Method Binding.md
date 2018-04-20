* Problem: when assigining a function to another function, the binding is lost. (ie. the new function no longer reference to the original function)

```jsx
/*-------------------
	Errors!!!
-------------------*/
const obj = {
	name: 'Peter',
	getName() {
		return this.name;
	}
};

const getName = obj.getName;

console.log(getName());
```

the getName function does not have `this`. Similar to a function, where `this` is not binded:

```jsx
const func = function() {
  console.log(this);
}
func(); // error
```

# Solution
* Use the function .bind() to reset the context
* Can bind to any object

```jsx
const obj = { ... };
const getName = obj.getName.bind(obj);
console.log(getName()); // Works
```

```jsx
const obj = { ... };
const getName = obj.getName.bind({ name: 'Peter' });
console.log(getName()); // Works
```

# (Not so efficient) Solution in component
* In this code, the function is bind() inside the render function. The drawback is that whenever the component is render, it binds again and again. It is quite expensive.

```jsx
class Options extends React.Component {
	handleRemoveAll() {
		console.log(this.props.options);
	}
	render() {
		return (
			<div>
			/*-------------------
      	.bind(this) inside render()
      -------------------*/
				<button onClick={this.handleRemoveAll.bind(this)}>Remove All</button>
				{
					this.props.options.map((option) => <Option key={option} optionText={option} />)
				}
			</div>
		);
	}
}
```

# (Real) Solution
* We bind the function inside `constructor`

```jsx
class Options extends React.Component {
	constructor(props) {
		super(props);
		/*-------------------
    	bind in constructor
    -------------------*/
		this.handleRemoveAll = this.handleRemoveAll.bind(this);
	}
	handleRemoveAll() {
		console.log(this.props.options);
	}
	render() {
		return (
			<div>
				<button onClick={this.handleRemoveAll}>Remove All</button>
				{
					this.props.options.map((option) => <Option key={option} optionText={option} />)
				}
			</div>
		);
	}
}
```

## Side note for `constructor()`
* Here is the basic code for `constructor()`
* By default, the `props` is passed into the constructor.

```jsx
constructor(props) {
	super(props);
	/* Additional code here */
}
```



