# CSS in JS

With the rise of component based frontend frameworks and the focus to keeping presentation layer in one file, CSS in JS came into spotlight.

## How are styles handled

As the name suggests, you can write CSS styles directly into your component's JS file. in many cases you can also make styles adaptive by using JS interpolations inside your CSS template literal.

from [Styled components docs:](https://styled-components.com/docs/basics#adapting-based-on-props)

```
const Button = styled.button`
  /* Adapt the colors based on primary prop */
  background: ${props => props.primary ? "palevioletred" : "white"};
  color: ${props => props.primary ? "white" : "palevioletred"};

  font-size: 1em;
  margin: 1em;
  padding: 0.25em 1em;
  border: 2px solid palevioletred;
  border-radius: 3px;
`;

render(
  <div>
    <Button>Normal</Button>
    <Button primary>Primary</Button>
  </div>
);
```

these styles are evaluated and injected during runtime. depending on use case and how css heavy and application is, this approach can be either faster or slower than sending an entire css file with payload.

injecting styles is primarily done with either using `<style>` tags or directly manipulating `CSSStyleSheet API`

When using SSR styles are always appended as a `<style>` tag inside the `<head>` of the rendered HTML page as it makes for a faster initial paint.
