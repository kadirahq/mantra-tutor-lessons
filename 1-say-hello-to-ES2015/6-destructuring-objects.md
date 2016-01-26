```
name: Destructuring Objects like a Guru
bulletPackage: free
```

With ES2015, we can destructure values inside objects and arrays very easily. For example, have a look at the following code:

~~~js
const user = {
    name: 'Arunoda',
    age: 80,
    city: 'Colombo'
};

const {name, age} = user;
console.log(name, age);
~~~

Here we simply extract the `name` and `age` fields of the user object.

There's more. Let's learn.

*****

```
id:     with-functions
type:   mcq
points: 15
```

This is extremely useful when used with functions. Have a look at the following code:

~~~js
function printName({name}) {
    console.log('Name is: ' + name);
}

const user = {
    name: 'Arunoda',
    age: 80,
    city: 'Colombo'
};
printName(user);
~~~

This not only simplifies our code, but it also self-documents the code. When we look at the first line of the function, we know exactly which fields of the input object we are using.

Now have a look at this code:

~~~js
function printUser({name, age = 20}) {
    console.log('Name is: ' + name + ' Age: ' + age);
}
~~~

What are/is the objects you can pass to the above function to get a result like this:

~~~
Name is: John Age: 20
~~~

  1. {name: 'John', age: 20, city: 'Colombo'}
  2. {name: 'John'}
  3. {name: 'John', agi: 30, city: 'Nigeria'}
  4. {nami: 'John', age: 20, city: 'Nigeria'}

Select from the select below:

 - 1
 - 1, 2
 - **1, 2, 3**
 - 1, 2, 3, 4

 *****

 ```
 id:     carefully-answer
 type:   text
 points: 5
 ```

The result is `1, 2, 3`. That's because:

* In the first case, you provide the age as 20.
* In the second case, age is not defined so it gets the default value (20).
* In the third case also, age is not defined.

---

Just like objects, you can destructure values from arrays as well. Have a look at this example:

~~~js
function printUser([name, age = 20]) {
    console.log('Name is: ' + name + ' Age: ' + age);
}

printUser(["Arunoda", 80]);
~~~
