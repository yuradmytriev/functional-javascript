Memoization is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again

Memoizing in simple terms means memorizing or storing in memory. A memoized function is usually faster because if the function is called subsequently with the previous value(s), then instead of executing the function, we would be fetching the result from the cache.

```js
const memo = (fn, cache = {}) => 
    (...args) => 
      cache[args] || (cache[args] = fn(...args));


const double = value => console.log('Computed!') || value * 2;


const doubleMemo = memo(double);


console.log(doubleMemo(5));
console.log(doubleMemo(5));

// Computed!
// 10
// 10
```

Memoization with Map:

```js
const memoize = fn => {
  const cache = new Map();
  const cached = function(val) {
    return cache.has(val) ? cache.get(val) : cache.set(val, fn.call(this, val)) && cache.get(val);
  };
  cached.cache = cache;
  return cached;
};
```
