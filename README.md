# rfc-js-optional-destructuring
A proposal for JS to support optional values during destructuring.

When we have an object out of which we want to select some deep fields,
we either reach for destructuring or optional chaining.

We can use `= {}` defaulting at each level, but this is verbose and hard to read, and often TypeScript complains about these default objects not conforming to the expected types.

```js
const { nest: { value1, deep: { value2 } = {} } = {} } = object
```

We could use `?:` like TypeScript to support per-field optionality:

```ts
const { nest?: { value1, deep?: { value2 } } } = object

// now we have `value1` and `value2` with their values or `undefined`.
```

Also, maybe we could apply optionality to the whole expression with `?` prefix or suffix:

```js
const ? { nest: { value1, deep: { value2 } } } = object
```

or:

```js
const { nest: { value1, deep: { value2 } } } ? = object
```

or maybe a `safe` or `optional` keyword for better readability:

```js
const safe { nest: { value1, deep: { value2 } } } = object
```

```js
const optional { nest: { value1, deep: { value2 } } } = object
```
