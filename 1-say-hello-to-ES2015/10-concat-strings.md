```
name: Concat Strings the Python Way
bulletPackage: free
```

It was always hard to concat strings in JavaScript. You had to use the `+` operator or use something like underscore templates.

With ES2015 template strings, now it's pretty easy. Have a look at the following example:

~~~js
const name = "Arunoda";
const welcome = `Hello ${name}, Good Morning!`;

console.log(welcome);
~~~

Note the use of " ` " when creating the string.

### Multiline Strings

As a result of support for template strings, now we can write multiline strings very easily. See:

~~~js
const message = `
  # Title

  This is a multi line string as markdown.
  It's pretty nice.
`;
console.log(message);
~~~

If there were no template strings, we would have to write it like this:

~~~js
var message = "\n  # Title\n\n  This is a multi line string as markdown.\n  It's pretty nice.\n";
console.log(message);
~~~
