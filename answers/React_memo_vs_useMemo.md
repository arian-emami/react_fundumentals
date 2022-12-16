# React.memo vs useMemo()

## useMemo():

useMemo is typically used when we want to prevent excessive invocation of an expensive function on each render. It takes a function to memorize and a dependency list. As long as dependency remains unchained function wont be recalculated.
from useMemo source code:

```
const prevDeps: Array<mixed> | null = prevState[1];
if (prevState !== null) {
    // return previous value if dependencies haven't changed
    if (areHookInputsEqual(nextDeps, prevDeps)) {
        return prevState[0];
    }
}

const nextValue = nextCreate();
hook.memoizedState = [nextValue, nextDeps];
return nextValue;
```

## React.Memo:

As the naming suggests, React.Memo is not a hook. React.Memo is a higher order component and is usually used for heavy components and nodes that are high in component tree.

from documentation:

> If your component renders the same result given the same props, you can wrap it in a call to React.memo for a performance boost in some cases by memoizing the result. This means that React will skip rendering the component, and reuse the last rendered result.

> React.memo only checks for prop changes. If your function component wrapped in React.memo has a useState, useReducer or useContext Hook in its implementation, it will still rerender when state or context change.

it is important to note that components props are checked using shallow comparison, meaning nested changes might not be detected.

```
const MyComponent = React.memo(function MyComponent(props) {
/* render using props */
/* if props are unchanged, will not rerender */
});
```

## useCallback():

useCallback lets yo memorize a function between renders. it takes a function and an array of dependency list. function wont be re-declared if nothing in dependency list is changed.

From React documentation:

```
function ProductPage({ productId, referrer, theme }) {
  // Every time the theme changes, this will be a different function...
  function handleSubmit(orderDetails) {
    post('/product/' + productId + '/buy', {
      referrer,
      orderDetails,
    });
  }

  return (
    <div className={theme}>
      {/* ... so ShippingForm's props will never be the same, and it will re-render every time */}
      <ShippingForm onSubmit={handleSubmit} />
    </div>
  );
}
```

### useCallback() vs useMemo():

while the API for both of them are the same, they do different things. useCallback() returns its function uncalled while useMemo() calls its function and returns the result

```
useCallback(fn, deps);
useMemo(fn, deps);
```
