# ClientSide routing VS ServerSide routing

## Server Side Routing

For traditional web pages and before AJAX, server side routing was the only option. in server side routing, request will be sent from client to the server as a url. server then response with an HTML page for that url. this process triggers the following actions in client's browser:

- Changes the url in browser's address bar
- Browser will discard the old page and renders the newly received one

with server side routing people can share specific pages from a website just by sharing an url.

## Client Side Routing

With the Rise of SPAs client side routing has been a surge in interest. in client side routing, links are handled with javascript. for example:

- browser detects a click on link and calls the appropriate event handler
- some client side code detects that th link is not external and prevents browser to make an GET request (prevents from browser's default behavior)
- if additional information is needed the client side code makes the necessary requests
- client side code changes the address bar url by using using the HTML5 history API, or maybe URL hashbangs on older browsers
- client side code renders the state changes and commits the result in the browser's view

## Hybrid approach

today needs of web applications require both the app like feel of client side routing and sharable urls and SEO friendliness of server side routing.
some meta-frameworks such as Nextjs have functionalities that can help you to benefit from client side and server side routing at the same time
