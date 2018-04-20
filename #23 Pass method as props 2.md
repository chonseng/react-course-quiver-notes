* Situation: we want to let `AddOption` component to change the `state.option`. And at same time, we want the `AddOption` component to handle the error by setting the state for its own.
* Instead of directly doing `onSubmit={this.props.handleAddOption}`, we do `onSubmit={this.handleAddOption}`. We still call the local method inside `AddOption`. And we add get the return value(the error message) from `this.props.handleAddOption`, and change the state in `AddOption`.

```jsx
class IndecisionApp extends React.Component {
	constructor(props) {
		super(props);
		/*-------------------
    	1. Bind
    -------------------*/
		this.handleAddOption = this.handleAddOption.bind(this);
		this.state = {
			options: []
		}
	}
	/*-------------------
  	2. The method to pass down
  -------------------*/
	handleAddOption(option) {
	  /*-------------------
    	Return error message for the child to display it
    -------------------*/
		if (!option) {
			return 'Enter valid value to add item';
		} else if (this.state.options.indexOf(option) > -1) {
			return 'This option already exists';
		}

		this.setState((prevState) => {
			return {
				options: prevState.options.concat(option)
			}
		})
	}
	render() {
		return (
			<div>
			  /*-------------------
        	3. Pass Down
        -------------------*/
				<AddOption 
					handleAddOption={this.handleAddOption}
				/>
			</div>
		);
	}
}

class AddOption extends React.Component {
	constructor(props) {
		super(props);
		/*-------------------
    	4. Since we are using `this` in `handleAddOption`, we want to bind `this`
    -------------------*/
		this.handleAddOption = this.handleAddOption.bind(this);
		this.state = {
			error: undefined
		};
	}
	/*-------------------
  	5. The local method to change the state of error
  -------------------*/
	handleAddOption(e) {
		e.preventDefault();

		const option = e.target.elements.option.value.trim();
		const error = this.props.handleAddOption(option);
		
		this.setState(() => {
			return {
				error // ES6 Syntax. same as error: error
			}
		})
	}
	render() {
		return (
			<div>
  			/*-------------------
        	Show error message
        -------------------*/
				{this.state.error && <p>{this.state.error}</p>}
				/*-------------------
        	6. Set the onSubmit method to the one in this component
        -------------------*/
				<form onSubmit={this.handleAddOption}>
					<input type="text" name="option" />
					<button>Add Option</button>
				</form>
			</div>
		);
	}
}
```