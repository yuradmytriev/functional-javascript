```js
const data = {
  list: {
    person: {
      profile: {
        name: 'John',
      }
    }
  }
};


const getData =
  (list) =>
  (person) =>
  (profile) =>
  (name) => name;


const getList = getData('list');
const getPerson = getList('person');
const getProfile = getPerson('profile');
const getName = getProfile('name');

console.log(getName);
```
