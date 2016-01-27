```
name: Introduction to ES2015
bulletPackage: free
```
Have you ever tried reading the source code of a newer JavaScript app or module? For example, try understanding the following code:

~~~js
// lib/vehicle.js
export default class Vehicle {
  constructor(type, number) {
    this.type = type;
    this.number = number;
    this.fuel = 1000;
  }

  start() {
    this._startHandler = setInterval(() => {
      this.fuel--;
    }, 500);
  }

  stop() {
    clearInterval(this._startHandler)
  }

  display() {
    return `Number: ${this.number}`;
  }
}

// main.js
import Vehicle from './lib/vehicle';
const {log} = console;

let v1 = new Vehicle('Car', 'HY-8244');
v1.start();
log(v1.display());
~~~

If you look at it carefully, it's pretty. But it's not the JavaScript you're used to writing, it's something else.

**That’s ES2015 and the New JavaScript**

Recently, JavaScript got a lot of **new features** to the language. Many more features have been suggested and they will be added to the language soon.

Interestingly, the JavaScript community started to use these new features **even before** they were fully implemented by browsers (and Node.js). That's because these features are pretty awesome and save us from doing a lot of hacks. And it's possible to use before it's fully supported in browsers thanks to transpilers like [Babel](https://babeljs.io/)

In this course, we are going see some of these features and their **real-life use cases**. Then you will understand ES2015 pretty well and use the features in your projects.

## Setting Up

In this course, we'll use a lot of ES2015 code and some traditional JavaScript code. Sometimes, we will ask you questions.

> You can skip these questions, but they are very simple and will verify your understanding of the topic. So, we really encourage you to work on them.

In the questions, usually you need to experiment with some code.

For that, you can use [this JSBin environment](https://jsbin.com/defeba/edit?js,console).

Sometimes, using that environment is not enough but we'll tell you how to run the code.

Now, everything is ready. It's time to try some ES2015.

Let’s get started!
