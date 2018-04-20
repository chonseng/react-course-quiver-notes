```jsx
let count = 0;
const addOne = () => {
	count += 1;
	renderCounterApp();
};

const renderCounterApp = () => {
	const templateTwo = (
		<div>
			<h1>Count: {count}</h1>
			<button onClick={addOne}>+1</button>
			<button onClick={minusOne}>-1</button>
			<button onClick={reset}>reset</button>
		</div>
	);
	ReactDOM.render(templateTwo, appRoot);
}

renderCounterApp();
```

Here, we manually render the DOM every time the button is clicked. Later, we will use react component to this for us. This is what it do behind the scene.

Note that even though it seems like it render the whole DOM every time, React helps us to render only the changed part(eg. the count).