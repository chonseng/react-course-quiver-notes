DOM attributes supported by React
=================================

Since “class” is a reserved word in JS, in JSX, we need to use “className” instead.

Look at <https://reactjs.org/docs/dom-elements.html> for more DOM attributes (Find the boxes down below for a full list)

onClick Event
=============

```jsx
const addOne = () => {
	console.log('addOne');
};

const templateTwo = (
	<div>
		<button onClick={addOne}>+1</button>
	</div>
);
```