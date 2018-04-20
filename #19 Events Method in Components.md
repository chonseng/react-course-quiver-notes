* In #12, we bind the submit function of the form to a global function `onFormSubmit`. Now, in components, we can create the function inside.

```jsx
class AddOption extends React.Component {
	handleAddOption(e) {
		e.preventDefault();

		const option = e.target.elements.option.value.trim();
		if (option) {
			alert(option);
		}
	}
	render() {
		return (
			<div>
				<form onSubmit={this.handleAddOption}>
					<input type="text" name="option" />
					<button>Add Option</button>
				</form>
			</div>
		);
	}
}
```