Look at <https://reactjs.org/docs/events.html> for the React events handler

## Key Ideas
* get the value inside the form: `const option = e.target.elements.option.value;`
* form and onSubmit event handler: 
```jsx
<form onSubmit={onFormSubmit}>
	<input type="text" name="option"/>
	<button>Add Option</button>
</form>
```

# Full Code

```jsx
const app = {
	title: "Indecision App",
	subtile: "whatever subtitle",
	options: []
}

const onFormSubmit = (e) => {
	e.preventDefault(); // Prevent refresh
  
  
  /*-------------------
	  e.target: the form
	  e.target.elements: give a list of the children. The "name" is the key that can be accessed
	  e.target.elements.option: option is the "name='option'"
  -------------------*/
	const option = e.target.elements.option.value;

	if (option) {
		app.options.push(option);
		e.target.elements.option.value = '';
	}
	render();
}

const onRemoveAll = () => {
	app.options = [];
	render();
}


const appRoot = document.getElementById('app');

const render = () => {
	const template = (
		<div>
			<h1>{app.title}</h1>
			{app.subtile && <p>{app.subtile}</p>}
			<p>{app.options.length > 0 ? "Here are your options" : "No options"}</p>
			<p>{app.options.length}</p>
			<button onClick={onRemoveAll}>Remove All</button>
			<ol>
				<li>Item one</li>
				<li>Item two</li>
			</ol>
			/*-------------------
      	Form
      -------------------*/
			<form onSubmit={onFormSubmit}>
				<input type="text" name="option"/>
				<button>Add Option</button>
			</form>
		</div>
	);

	ReactDOM.render(template, appRoot);
}

render();
```