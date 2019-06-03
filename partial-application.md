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
