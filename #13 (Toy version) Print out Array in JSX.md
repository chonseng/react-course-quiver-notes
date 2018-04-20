```jsx
/*-------------------
	Basic One (Not practical)
-------------------*/
// Can't add two same item here since the key needs to be unique
{
	app.options.map((opt) => <li key={opt}>{opt}</li>)
}
```