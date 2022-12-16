# Difference between Next.js ISR, SSR, CSR

## Client Side Rendering (CSR):

The way that a typical react app renders content is the following:

- Send an html with an empty div as React's root node
- Wait for React and other necessary JS libraries to load
- React uses the root node as the starting point of the virtual DOM
- Necessary request and useEffects will be fired
- React commits the appropriate changes to the browser DOM

As you can see there are a lot of steps and we won't see any content on the screen until the last step. In other words, the **time to content** is high.

## Server Side Rendering (SSR):

In order to solve CSR time to content issues we can use Server Side Rendering. As the name implies, it performs part of the initial rendering on the server at request time rather than in the client's browser.

The steps are as follows:

- Make the necessary requests in the get-server-side-props function and pass that data as props to the page
- Pre-render React initial commits to the DOM
- Send initial commits as plain HTML to the client. This makes for a fast first loading of the page and the initial content will be visible quickly.
- Load React and other necessary scripts.
- In the payload also include a set of instructions for hydrating the app and passing the control to React DOM

### Hydration:

The process in which the client's React DOM takes over server side rendered content

From [Nect.js Docs:](https://nextjs.org/learn/foundations/how-nextjs-works/rendering)
![pre rendering](../_img/pre-rendering.png)

## Incremental static regeneration (ISR):

One disadvantage of server-side rendering is the rather long response time. The problem is that the Nextjs server needs to fetch data, pass it as props, render the page and then send the response. We can use static site generation at build time but that wouldn't be handy for websites with dynamic contents such as E-commerce, CRMs and etc. .

Enter incremental static regeneration. In this mode pages will be rendered at build time and can be rebuilt in the future without needing to rebuild the entire site.

This code snippet from Nextjs docs describes it best

```
export async function getStaticProps() {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  return {
    props: {
      posts,
    },
    // Next.js will attempt to re-generate the page:
    // - When a request comes in
    // - At most once every 10 seconds
    revalidate: 10, // In seconds
  }
}
```
