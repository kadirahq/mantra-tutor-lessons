```
name: Immutability in JavaScript
bulletPackage: free
```

These days in JavaScript, we try to follow functional programming concepts. So, we try to write pure functions as much as we can.

> That means, a function gets some input and returns some value. But the function does not change the values it receives via arguments. And it always returns the same value for the same input. 
>
> `random()` would not a pure function. And any function that modifies some global state is also not pure.

Previously to do this, we needed to write some more code or use of utility libraries. But now it's pretty simple with the **spread operator**.

Have a look at the following examples:

#### With Objects
~~~js
function addMarks(user, marks) {
  return {
    ...user,
    marks
  };
}

const user = {username: 'arunoda'};
const userWithMarks = addMarks(user, 80);

console.log(user, userWithMarks);
~~~

#### With Arrays
~~~js
function addUser(users, username) {
  const user = {username};
  return [
    ...users,
    user
  ];
}

const user = {username: 'arunoda'};
const users = [user];
const newUsers = addUser(users, 'john');

console.log(users, newUsers);
~~~
