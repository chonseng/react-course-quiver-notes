```jsx
class IndecisionApp extends React.Component {
	render() {
		return (
			<div>
				<Header />
				<Action />
				<Options />
				<AddOption />
			</div>
		);
	}
}

ReactDOM.render(<IndecisionApp />, document.getElementById('app'));
```