```jsx
<button disabled={app.options.length === 0} onClick={onMakeDecision}>What should I do?</button>
```

If the statement is evaluated to true, that is `disable={true}`, then the DOM will render `<button disabled></button>` 