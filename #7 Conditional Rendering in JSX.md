```jsx
<p>{age >= 18 ? "Adult" : "Kid"}</p>
{age && <p>{age}</p>} // Output the p tage if age "exists"
{foo(age)} // Output the return value of the function

// Evaulate to nothing
{undefined}
{null}
{true}
{false}
```