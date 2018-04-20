1. Setup default state object
2. Component rendered with default state values
3. Change state based on event
4. Component re-rendered using new state values
5. Start again at 3

## `setState()`
* Use `setState` to change the state
* The previous state is passed in as the first argument. If we don't need it, it can be empty.
* return an object containing the changes you want. It is not overriding the whole state as the return object. React will only change the things that is inside the return object.
* (eg. Here, if `this.state = { count: 0, name: 'Peter' }`, the `name` will stay unchange.

```jsx
this.setState((prevState) => {
	return {
		count: prevState.count + 1
	};
});

this.setState(() => {
	return {
		count: 0
	};
});
```

# Full Code

```jsx
class Counter extends React.Component {
	constructor(props) {
		super(props);
		this.handleAddOne = this.handleAddOne.bind(this);
		this.handleMinusOne = this.handleMinusOne.bind(this);
		this.handleReset = this.handleReset.bind(this);
		this.state = {
			count: 0
		};
	}
	handleAddOne() {
		this.setState((prevState) => {
			return {
				count: prevState.count + 1
			};
		});
	}
	handleMinusOne() {
		this.setState((prevState) => {
			return {
				count: prevState.count - 1
			};
		});
	}
	handleReset() {
		this.setState(() => {
			return {
				count: 0
			};
		});
	}
	render() {
		return (
			<div>
				<h1>Counter: {this.state.count}</h1>
				<button onClick={this.handleAddOne}>+1</button>
				<button onClick={this.handleMinusOne}>-1</button>
				<button onClick={this.handleReset}>Reset</button>
			</div>
		);
	}
}
```