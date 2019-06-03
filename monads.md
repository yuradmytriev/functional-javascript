#### Identity monad

  
```js
function Identity(value) {

  this.value = value;

}

Identity.prototype.bind = function(transform) {

  return transform(this.value);

};

Identity.prototype.toString = function() {

  return 'Identity(' + this.value + ')';

};

var result = new Identity(5).bind(value =>

  new Identity(6).bind(value2 =>

    new Identity(value + value2)));

```
 
#### Continuation monad

 
The continuation monad is used for asynchronous tasks. Fortunately with ES6 there is no need to implement it — the Promise object is an implementation of this monad. 
Promises are similar to monads cuz they wrap value into their Promise type and with then function they return promise.

```js
Promise.resolve(value)
``` 

wraps a value and returns a promise (the unit function). 

```js
Promise.prototype.then(onFullfill: value => Promise) 
```

takes as an argument a function that transforms a value into a different promise and returns a promise (the bind function).

  
```js
var result = Promise.resolve(5).then(function(value) {

  return Promise.resolve(6).then(function(value2) {

    return value + value2;

  });

});

result.then(function(value) {

  print(value);

});
```
