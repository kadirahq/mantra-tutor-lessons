```
name: Clean up your Code with Arrow Functions
bulletPackage: free
```

We can use arrow functions to clean up our code base. Basically, we can use arrow functions as [lambdas](https://en.wikipedia.org/wiki/Anonymous_function).

This should be familiar to you:

~~~js
const numbers = [10, 20, 30, 50];
const multiplyBy10 = numbers.map(function(a) {
    return a * 10;
});
console.log(multiplyBy10);
~~~

With arrow functions, you can write the same code block like this:

~~~js
const numbers = [10, 20, 30, 50];
const multiplyBy10 = numbers.map(a => a * 10);
console.log(multiplyBy10);
~~~

**Wow! That's cool right?**

There's more you can do with arrow functions.

*****

```
id:     more-on-arrows
type:   mcq
points: 15
```

If your method accepts more than one value as arguments, you can write it like this:

~~~js
const numbers = [10, 20, 30, 50];
const multiplyByIndex = numbers.map((a, i) => a * i);
console.log(multiplyByIndex);
~~~

Great. Now, let's try to do a simple task.

Here's a slightly different version of the above code block:

~~~js
const numbers = [10, 20, 30, 50];
const multiplyBy10 = numbers.map(a => {res: a * 10});
console.log(multiplyBy10);
~~~

So, what'll be the final result:

  - [{"res":100},{"res":200},{"res":300},{"res":500}]
  - **[undefined, undefined, undefined, undefined]**
  - [{"res":10},{"res":20},{"res":30},{"res":50}]
  - [{"res":1000},{"res":2000},{"res":3000},{"res":5000}]

*****

```
id:     more-on-arrows-answer
type:   text
points: 5
```

Interestingly, answer is `[undefined, undefined, undefined, undefined]`. That's because our arrow function thinks `{res: a * 10}` is a block. So, in this case, you need to wrap it in parentheses like this:

~~~js
const numbers = [10, 20, 30, 50];
const multiplyBy10 = numbers.map(a => ({res: a * 10}));
console.log(multiplyBy10);
~~~
