A higher order function is a function that takes a function as an argument, or returns a function.

HOC helps us create abstractions. Abstractions hide details and give us the ability to talk about problems at a higher (or more abstract) level.

Receives a function as an argument:

const array = [1, 2, 3];


// argument function
const double = (item) => item * 2;


// map function takes another function as argument
const transformedArray = array.map(double);


console.log(transformedArray);

Custom hight-order function:

const customMap = (array, fn) => {
    const newArray = [];
  
    for (let i = 0; i < array.length; i++) {
      newArray.push(fn(array[i]));
  }
  
  return newArray;
};

HOC. Also helps us to reuse our code and make it more reusable. 

Here is a function `repeatLog` where we use log function n-count times. And the main problem here that we cannot reuse this with another action.

function repeatLog(n) {
  for (let i = 0; i < n; i++) {
    console.log(i);
  }
}

So we can move our logic to another function or action and use this action with our code.

function repeat(n, action) {
  for (let i = 0; i < n; i++) {
    action(i);
  }
}

repeat(3, console.log);

Return a function:

const greaterThan = n => m => m > n;

const isGreaterThan10 = greaterThan(10);

console.log(isGreaterThan10(11)); // → true

Another example:

const minOfArgs = (f) => (...args) => f(...args);


minOfArgs(Math.min)(3, 2, 1);
