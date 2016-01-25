```
name: Stop Writing "self=this"
bulletPackage: free
```

I hope you have used the `self=this` code block, especially when working with classes. Have a look at the following code:

~~~js
function Clock() {
    this.currentTime = new Date();
}

Clock.prototype.start = function() {
    var self = this;
    setInterval(function() {
        self.currentTime = new Date();
    }, 1000);
}
~~~

With ES2015, we can avoid `self=this` with arrow functions like this:

~~~js
function Clock() {
    this.currentTime = new Date();
}

Clock.prototype.start = function() {
    setInterval(() => {
        this.currentTime = new Date();
    }, 1000);
}
~~~

Here, we've used an arrow function for the `setInterval`. It carries the context (`this`) of the start method.

**Isn't that great?**

Let's learn more.

*****

```
id:     carefully
type:   mcq
points: 20
```

Even though arrow functions are great, you need to use them carefully.

To demonstrate this, let’s try an example.

Imagine we have a RPC system and we are defining a method on that RPC system. We use an arrow function to create that method. Inside that method, we can access the current user's userId with `this.userId`.

> In the following example, assume there is a logged-in user:

~~~js
RPC.methods.sum = (a, b) => {
  if (!this.userId) {
    throw new Error("Unauthorized");
  }

  return a + b;
}

const total = RPC.call('sum', 10, 20);
console.log('Total is: ' + total);
~~~

[Try the above code](https://jsbin.com/zuseqap/edit?js,console).

What was the output?

 - Total is: 30
 - **An error saying `this.userId` is not defined**
 - Total is:30
 - An error saying `RPC` is not defined

 *****

 ```
 id:     carefully-answer
 type:   text
 points: 5
 ```

As you have seen, even though we have `userId` in this context, we can't access it using `this`. That's because arrow functions carry the context of the place where the function is defined. They mask the runtime context.

To avoid this issue, you need to use a traditional function like this:

~~~js
RPC.methods.sum = function (a, b) {
  if (!this.userId) {
    throw new Error("Unauthorized");
  }

  return a + b;
}
~~~

[Try the above code](https://jsbin.com/botime/edit?js,console).

So, here's a point to keep in mind.

> Arrow functions are great, but they are not a solution you can use everywhere. Think before using them.
