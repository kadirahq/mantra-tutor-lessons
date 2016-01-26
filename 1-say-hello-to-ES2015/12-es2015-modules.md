```
name: ES2015 Module System
bulletPackage: free
```

ES2015 has a module system, which we can use to organize our app into smaller, manageable modules. This module system is very similar to the CommonJS module system (or the module system of Node.js), but with **one major** difference. Here it is:

> All the imports should be static. That means, you can't import modules at runtime. They need to done at compile time (or better when interpreting JavaScript).
> Here's a piece of code that **cannot** be written with ES2015 modules:

~~~js
let router;

if (typeof window === 'function') {
  router = import './client-router';
} else {
  router = import './server-router';
}
~~~

Let's get started.

*****

```
id:     setting-up
type:   text
points: 5
```

## Setting Up

In this lesson, we need to try out some code. But, there is no way we can try these modules on the browser. For this, we need to use a simple Node.js app. So, you need to have Git and Node.js installed on your system.

Let's clone the following repo:

~~~
git clone https://github.com/kadira-samples/es2015-module-sample.git
~~~

Then go inside it and run: `npm install`.

Now, we are ready. It's time to get started.

*****

```
id:     named-exports
type:   mcq
points: 20
```

### Named Exports

Here, we simply export a simple function called `sum`, which is defined in `src/lib/math.js` like this:

~~~js
export function sum(a, b) {
    return a + b;
}
~~~

Then we import it from the `src/main.js` module and invoke it like this:

~~~js
import {sum} from './lib/math';

const total = sum(10, 20);
console.log(total);
~~~

Then you can run it by invoking the following command:

~~~
node run.js
~~~

> Make sure to use `{sum}` when importing.
> Let's imagine there is another function called `multiply` in the `src/lib/math.js` module. Then, we write our import code like this: `import {sum, multiply}`.

Just like functions, we can export any type of variable including classes. See the following examples:

~~~js
export const BASE = 10;
export let name = 'Arunoda';
export class Vehicle {};
~~~

So, now it's time for a quiz.

Here, we have listed some different ways to export the `sum` function. Some of them are incorrect. Find the correct ways.

Method 1:
~~~js
function add(a, b) {
    return a + b;
}
export const sum = add;
~~~

Method 2:
~~~js
export const sum = (a, b) => {
    return a + b;
}
~~~

Method 3:
~~~js
const sum = (a, b) => {
    return a + b;
}
export sum;
~~~

Method 4:
~~~js
export function(a, b) {
    return a + b;
}
~~~

  - Method 1
  - **Methods 1 and 2**
  - Methods 2 and 3
  - Methods 1 and 3

*****

```
id:     default-export
type:   mcq
points: 25
```

### Default Export

Sometimes we need to export a single module rather than exporting a named export. We call these default exports. Here's how to do them. Look at `src/lib/vehicle.js`.

Here's what it looks like:

~~~js
export default class {
  constructor(type, number) {
    this.type = type;
    this.number = number;
  }

  display() {
    return `Number: ${this.number}`;
  }
}
~~~

Then, you can import it like this:

~~~js
import Vehicle from './lib/vehicle';

const v1 = new Vehicle('Car', 'GH-3355');
console.log(v1.display());
~~~
> You can write above code on `src/main.js`

In the above `src/lib/vehicle.js` module, we've also exported a function called `print`. How can we import it?

Option 1:
~~~js
import Vehicle, print from './lib/vehicle';
~~~

Option 2:
~~~js
import {Vehicle, print} from './lib/vehicle';
~~~

Option 3:
~~~js
import Vehicle from './lib/vehicle';
import {print} from './lib/vehicle';
~~~

Option 4:
~~~js
import Vehicle, {print} from './lib/vehicle';
~~~


  - Option 1
  - Option 2
  - **Option 3**
  - Option 4

*****

```
id:     default-export-answer
type:   text
points: 5
```

Here the correct answer is option 3, which is:

~~~js
import Vehicle from './lib/vehicle';
import {print} from './lib/vehicle';
~~~

That's how we can import both the default export and some named export inside the same module.

---

There are more things you can do with modules like renaming imports and importing all named exports at once. For that, have a look at the [MDN documentation](https://developer.mozilla.org/en/docs/web/javascript/reference/statements/import) on module imports.
