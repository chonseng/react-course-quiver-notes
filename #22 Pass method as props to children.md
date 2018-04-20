* Situation: We want the `Options` component (child of `IndecisionApp`) to delete the options. However, the child can't access the parent's state directly.
* To solve this, we make a method in the parent and pass it down to the child as a `props`. Thus, the child `Options` can call `this.props.handleDeleteOptions` to change the parent's `state`.

```jsx
class IndecisionApp extends React.Component {
	constructor(props) {
		super(props);
		/*-------------------
    	1. Bind
    -------------------*/
		this.handleDeleteOptions = this.handleDeleteOptions.bind(this);
		this.state = {
			options: ['Thing one', 'Thing two', 'Thing three']
		}
	}
	/*-------------------
  	2. Method we wanted to pass down
  -------------------*/
	handleDeleteOptions() {
		this.setState(() => {
			return {
				options: []
			}
		});
	}

	render() {
		return (
			<div>
				/*-------------------
        	3. Pass Down as props
        -------------------*/
				<Options 
					options={this.state.options} 
					handleDeleteOptions={this.handleDeleteOptions}
				/>
			</div>
		);
	}
}


class Options extends React.Component {
	render() {
		return (
			<div>
			  /*-------------------
        	4. Call the parent's function
        -------------------*/
				<button onClick={this.props.handleDeleteOptions}>Remove All</button>
				{
					this.props.options.map((option) => <Option key={option} optionText={option} />)
				}
			</div>
		);
	}
}
```