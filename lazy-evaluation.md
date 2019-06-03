Lazy evaluation is a strategy where the evaluation of a piece of code is deferred until its results are needed.

```js
const lazy =
  (creator, res) =>
  (...args) =>
  res || (res = creator(...args));


const double = value => console.log('Computed!') || value * 2;


const lazyFive = lazy(double);


console.log(lazyFive(5));
console.log(lazyFive(5));
```

Ленивые вычисления в javascript Ленивые, отложенные вычисления — такой подоход, когда значения вычисляются только тогда, 
когда в них возникает потребность, при этом есть возможность не вычислять это значение повторно при последующих вызовах 
функции. В javascript этот подход можно реализовать с помощью замыканий и переопределения функции изнутри самой себя. 

```js
let func = () => {
  const variable_foo = 5;
  console.log('Computed!');
  func = () => variable_foo * 2;
  return func();
};


console.log(func());
console.log(func());


// Computed!
// 10
// 10
```

Фишка заключается в том, что значения variable_foo и variable_bar будут вычислены только при первом вызове функции. 
При этом-же вызове функция переопределит себя, захватывая scope с вычисленными переменными и себя-же родимую вызовет 
(при этом корректно сохраняя this, возвращаемое значение, а так же переданные аргументы). Этот подход сработает и для 
методов: 

```js
const Math = {
  getValue(value) {
    console.log('Computed!');
    return value;
  },
  double(value) {
    const data = this.getValue(value);
    this.double = () => data * 2;
    return this.double();
  }
};

console.log(Math.double(5));
console.log(Math.double(5));

// Computed!
// 10
// 10
```

В данном примере функция range не вычисляется до того момента пока мы не вызовем метод first.

```js
const oneToInfinity = range(1, Infinity);
const oneToTen = oneToInfinity.first(10); 
```
