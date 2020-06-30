# ExampleCounter

Basic counter

## Dependencies

none

## Installation

- src/components.js
```js
/* ... */
export { default as ExampleCounter } from "./ExampleCounter/src/ExampleCounter.vue";
/* ... */
```

- src/sandbox.js
```js
export default {
    routes: [
    /* ... */
        {path: '/ExampleCounter', component: () => import('./ExampleCounter/sandbox/ExampleCounter.vue')},
    /* ... */
    ]
}
```
