```
name: Write Classes Like You Did with Java
bulletPackage: free
```

JavaScript was not a proper object-oriented language. But we used functions and prototypes to simulate classes in JavaScript. With ES2015, we don't need to hack it anymore. Now we can write classes natively.

This is how you can create a simple class:

~~~js
class Vehicle {
  constructor(type, number) {
    this.type = type;
    this.number = number;
  }

  display() {
    return `Number: ${this.number}`;
  }
}

const v1 = new Vehicle('Car', 'GH-2343');
console.log(v1.display());
~~~

> Behind the scenes, it's using functions and prototypes to implement the class.
> So, it's compatible with older versions of JavaScript while providing us with nicer syntax.
> That means you can still access the prototype and edit it as needed.

There's more you can do with classes. Let's learn.

*****

```
id:     extending
type:   mcq
points: 25
```

This is how you can extend a class:

~~~js
class Vehicle {
  constructor(type, number) {
    this.type = type;
    this.number = number;
  }

  display() {
    return `Number: ${this.number}`;
  }
}

class Car extends Vehicle {
  constructor(number) {
    super('Car', number);
  }

  display() {
    const value = super.display();
    return `Car ${value}`;
  }
}

const v1 = new Car('GH-2343');
console.log(v1.display());
~~~

Here we've extend the Vehicle into a Car. Have a look at these things:

* We called the super `constructor` (Vehicle's constructor) inside the Car constructor.
* We called `super.display()` inside the `display()` method of Car. This shows us how to override a method in a subclass.

**Now it' time for a simple task.**

Just remove the constructor in our Car class. Then, it should look like this:

~~~js
class Vehicle {
  constructor(type, number) {
    this.type = type;
    this.number = number;
  }

  display() {
    return `Number: ${this.number}`;
  }
}

class Car extends Vehicle {
  display() {
    const value = super.display();
    return `Car ${value}`;
  }
}

const v1 = new Car('GH-2343');
console.log(v1.display());
~~~

When you run the code above, the output looks like this: `Car Number: undefined`.

How do we get it as `Car Number: GH-2343` without changing the class?

  - There is no way to do that.
  - Create the car object like: new Car('GH-2343', 'Car');
  - **Create the car object like: new Car('Car', 'GH-2343');**
  - Create the car object like: new Car('GH-2343', null);

*****

```
id:     extending-answer
type:   text
points: 5
```

Here's the correct answer:

~~~js
new Car('Car', 'GH-2343')
~~~

Since we didn't implement the constructor for the Car class, it uses the constructor of the Vehicle. That's why we've to create the Car object as `new Car('Car', GH-2343')`, which satisfy Vehicle's constructor.
