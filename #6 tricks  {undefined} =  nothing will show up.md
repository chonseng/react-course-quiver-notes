```jsx
undefined, null, true, false in JSX will envaluate to nth
```

```jsx
function getLocation(location) {
	if (location) {
		return <p>Location: {location}</p>;
	}
	// Return undefined 
}

...
var x = (
  <div>
    <p>..</p>
    {getLocation(user.location)} // Nothing will show up if the return value is undefined
  </div>
);
```



