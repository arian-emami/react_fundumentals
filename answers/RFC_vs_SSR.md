# React Server Components vs Server Side Rendering

## Server Side Rendering:

The purpose of SSR is to speed up the time to content, better SEO and not much else. As we mentioned in previous questions, after hydration, a server side rendered page is the same as a normal, client side rendered react page.

## React Server Components:

A new addition to the React API is server components. As the name suggests server components are only rendered on the server and they are not even bundled in the client side package.

They are mainly aimed at data fetching and typically used to pass props to client components. it is important to note that props passed down by server components must be network serializable. For example you cant pass a function from a server component.
