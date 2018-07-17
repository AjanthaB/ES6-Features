# **ES-6 New Features**


- Variable Swapping
- Spread Operator
- Computed Properties
- Generators
- Destructuring (up to 2 or more)




## Variable Swapping

Now is't very easy to swap two variable.
``` js
var a = 10, b =20;

[a. b] = [b, a];

console.log(a, b);
// output 20, 10

```


## Spread Operator

Spread syntax allows an iterable such as an array expression or string to be expanded in places 
where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

### Spread in function calls

``` js

function func(x, y, z) { }
var args = [0, 1, 2];
func(...args);

```

### Spread in array literals

``` js
var nums = ['100', '200']; 
var lyrics = ['10', ...nums, '300', '400']; 
// ["10", "100", "200", "300", "400"]

```

Copy or Concat Arrays

``` js
// create a copy of array
var array = [1,2,3,4,5]
var copy = [..array]
// [1,2,3,4,5]

// concatenate arrays
var arr1 = [1,2,3]
var arr2 = [4,5,6]

var newArray = [...arr1, ...arr2]
// [1,2,3,4,5,6]

```

### Spread in object literals

Shallow-cloning (excluding prototype) or merging of objects is now possible using a shorter syntax than **Object.assign()**.

``` js
var obj1 = {a:10, b: 20}
var obj2 = {x: 30, y:40}

var newCopy = {...obj1}
// {a:10, b: 20}


var newObj = {...obj1, ...obj2}
// {a:10, b: 20, x: 30, y:40}

```

## Computed Properties

``` js

// Shorthand property names
var a = 'foo', b = 42, c = {};
var o = {a, b, c};
// {foo: 'foo', b: 'b', c: {}}

// Computed property names (ES2015)
var prop = 'foo';
var o = {
  [prop]: 'hey',
  ['b' + 'ar']: 'there'
};
// {'bar': "there"}


var o = {
  [(x => x % 2 === 0  ? 'even' : 'odd')(5)]: 5
}
// {odd: 5}


```

## Generators

Generators are functions which can be paused the execution and resume later. Their context (variable bindings) will be saved across re-entrances. 
Generators are very helpful when come promises. Now we can avoid **Callback Hell** still keeping the asynchronous manner and code looks like synchronous.

Calling a generator function does not execute its body immediately; an iterator object for the function is returned instead. When the iterator's next() method is called, the generator function's body is executed until the first yield expression, which specifies the value to be returned from the iterator or, with yield*, delegates to another generator function. The next() method returns an object with a value property containing the yielded value and a done property which indicates whether the generator has yielded its last value as a boolean. Calling the next() method with an argument will resume the generator function execution, replacing the yield expression where execution was paused with the argument from next(). 

When execution is finished, will return a generator object with a **done** set to **true** and result set to **value**.
Execution will finished if throws any errors inside the body. Errors needs to handle inside the body. otherwise will return a object as {value: undefined, done: true}.

``` js

function* increment() {
  var i = 0;
  while (i < i+1)
    yield i++;
}

var gen = increment();
console.log(increment.next()) // {value: 0, done: false}
console.log(increment.next()) // {value: 1, done: false}
console.log(increment.next()) // {value: 1, done: false}


// calculate fibonacci numbers
var fibonacci = function*(){
  let pre = 0, cur = 1;
   while (pre < 1000) {
     // Here we destruct the former state
     [pre, cur] = [cur, pre + cur];
     // and yield (return) each step
     yield pre;
   }
}();

for (var n of fibonacci) {
  console.log(n);
}
```


## Destructuring (up to 2 or more)



