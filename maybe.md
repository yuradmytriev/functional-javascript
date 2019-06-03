The maybe monad is similar to the identity monad but besides storing a value it can also represent the absence of any value.

  
```js
const isNullOrUndef = (value) => value === null || typeof value === "undefined";


const maybe = (value) => ({
  isNothing: () => isNullOrUndef(value),
  extract: () => value,
  map: (transformer) => !isNullOrUndef(value) ? Maybe.just(transformer(value)) : Maybe.nothing()
});

const Maybe = {
  just: maybe,
  nothing: () => maybe(null)
};

const a = {
  b: {
    c: "fp"
  }
};

const maybeA = Maybe.just(a)
  .map(a => a.b)
  .map(b => b.c)
  .map(c => c + " is great!");

console.log(maybeA.extract());
```
