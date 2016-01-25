```
name: Use let and const
bulletPackage: free
```

When declaring variables, we used to use `var`. But it has one big issue. Every variable we define with `var` has a functional scope. That leads to weird code like this (which leads to weird bugs, of course):

~~~js
for (var lc=0; lc < 10; lc++) {
  var value = lc;
}

console.log(value, lc);
~~~

See, you can access both `value` and `lc`, even though they are defined inside the `for` loop.

ES2015 just fixed this issue.

*****

```
id:     const-let
type:   mcq
points: 15
```

With ES2015, you can use `const` or `let` instead of `var`. They define block scope variables.

Here is an example:

~~~js
for (var lc=0; lc < 10; lc++) {
  let value = lc;
}

console.log(value); // throws an error
~~~

The variable `value` is only available within the `for` loop.

**Okay, then what's the use of `const`?**

`const` is just like `let`, but it won’t let you change the variable.

> In most cases, you can use `const` instead of `let`. That's how most developers declare variables with ES2015.

Now, let's try a simple question. Look at the following code:

~~~js
const user = {name: "Arunoda"};
user.name = "Susiripala";
console.log(user.name);
~~~

Does this code work?

  - **Yes. It works.**
  - No. It doesn't.

*****

```
id:     const-let-answer
type:   text
points: 5
```

The answer is yes. That's because, we are trying to change a field inside the variable `user`, but not the variable itself.

> That's why we said, everyone prefers to use `const` instead of `let`.
