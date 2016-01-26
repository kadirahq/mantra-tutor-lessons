```
name: Cloning and Merging Objects like a Pro
bulletPackage: free
```

In our apps, cloning and merging objects is one of core tasks we do. Usually, we use an [underscore](http://underscorejs.org/) or [lodash](https://lodash.com/) to do so.

Let's look at some examples:

~~~js
var user = {name: "Arunoda"};
var newUser = _.clone(user);
var withAge = _.extend(user, {age: 20});
var newUserVersion = _.defaults({age: 80}, user);

console.log(newUser, withAge, newUserVersion);
~~~
[Try the above code](http://jsbin.com/wubuku/edit?js,console).

In ES2015, there's an easy way acheive all of the above without any utility library. Let's try that.


*****

```
id:     es2015-way
type:   mcq
points: 25
```

## Cloning and Merging with ES2015

With ES2015, we can do this very easily without using a utility library. See the following examples:

~~~js
const user = {name: "Arunoda"};
const newUser = {...user};
const withAge = {...user, age: 20};
const newUserVersion = {age: 80, ...user};

console.log(newUser, withAge, newUserVersion);
~~~

Isn't that cool?

> When you are adding a new field to an object, it's good practice to create new objects rather than extending it.
> This leads to clear code and reduces mistakes.
> This new syntax encourages us to do that.

So, here a simple question for you. Check the following code:

~~~js
const user = {
  name: 'Arunoda',
  emails: ['hello@arunoda.io']
};

const newUser = {...user};
newUser.emails.push('mail@arunoda.io');

console.log(user.emails);
~~~

What'll be the result?

 - **["hello@arunoda.io", "mail@arunoda.io"]**
 - hello@arunoda.io, mail@arunoda.io"
 - ["hello@arunoda.io"]
 - hello@arunoda.io

 *****

 ```
 id:     es2015-way-answer
 type:   text
 points: 5
 ```

The correct answer is `["hello@arunoda.io", "mail@arunoda.io"]`. Even though we cloned the object, it's not a deep clone. We only cloned the top-level fields.

The arrays used in the `emails` field of both objects are the same.

*****

```
id:     array
type:   text
points: 5
```

## Adding Elements to Arrays

Just like objects, we can clone arrays too. See the following example:

~~~js
const marks = [10, 20, 30];
const newMarks = [...marks, 40];

console.log(marks, newMarks);
~~~
