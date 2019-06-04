Partial application produces functions of arbitrary number of arguments. The transformed function is different from the original — it needs less arguments.

Is a technique of fixing a number of arguments to a function, producing another function of smaller arguments

```js
const sum = (x, y) => x + y;

const sum5 = sum.bind(null, 5);

console.log(sum5(10)); // 15
```

Допустим у нас есть приложение где мы имеем слоенную архитектуру и хотим работать с данными в разных частях приложения. Мы в одной точке определяем нашу функцию по сбору данных потом на одном из слоев получаем первые данные для функции и на другом слое остальные данным и вызов функции. То есть частичное применение функции это когда мы привязываем к функции аргументы и возвращаем новую функцию с привязанными аргументами.

```js
const showData = (a, b) => console.log(a, b);

// in one part get data

const getFirstData = showData.bind(null, 'data');  

// in another part get another data

getFirstData('data1');
```

```js
 const db = {
   data: 'some data',
 };

 const getData = (db) => {
   const changedData = db.data + ' with some changes';

   return () => {
     console.log('write this data to fs ->', changedData)
   }
 };

 const writeChangedDataToFs = getData(db);

 writeChangedDataToFs();
 ```
