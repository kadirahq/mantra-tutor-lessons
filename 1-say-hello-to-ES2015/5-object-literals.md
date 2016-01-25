```
name: Say Hi to Improved Object Literals
bulletPackage: free
```

Most of the time, we create objects. Now, we've some features to make our life easier. Let us show you some of them.

With ES2015, you can define a function very easily inside an object. See:

~~~js
const user = {
    getName() {
        return 'Arunoda';
    }
}

console.log(user.getName());
~~~

With this, you don't need to write the `function` keyword every time.

**Here's the coolest feature you'll love the most:**

~~~js
const name = 'Arunoda';
const age = 80;

const user = {name, age};
~~~

See how easy it is. Otherwise, we'd have to write it like this:

~~~js
const name = 'Arunoda';
const age = 80;

const user = {
    name: name,
    age: age
};
~~~
