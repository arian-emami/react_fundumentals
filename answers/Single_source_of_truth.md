# Single source of truth and its importance in React

React encourages **on-way data binding** and **top-down data flow**. mening if two components need to share a state, that state should be lifted up to their closest common ancestor.
the reasoning behind this is the followings

- ## 1- Reduce the surface area for bugs
  - When something is not working properly you can just open React's devtools and follow the state along components tree.
- ## 2- Easy to implement custom logic
  - If a value can be derived from other states, it shouldn't be a state at all. we can always calculate this value in some component's render() function and on top of that we can implement any custom logic we need such as rounding, clearing inputs etc. .
