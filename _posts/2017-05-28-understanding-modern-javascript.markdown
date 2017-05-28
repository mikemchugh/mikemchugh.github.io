---
layout: post
title:  "Understanding modern JavaScript - let and const"
date:   2017-05-28 10:00:00 +0100
categories: JavaScript ES2015
---

# Understanding modern JavaScript

My JavaScript is a little rusty so I decided to invest some time in learning some of the newer features added in the last few years.

It's a little confusing when people reference different version names but from what I know ES2015 was formally known as ES6 and ES2016 was formally known as ES7.

We'll start with `let` and `const`.

## let vs var

`let` is the way of declaring a variable with block scope, `var` declares a variable with function scope. I feel this is a massive improvement for people new to JavaScript; when I started the use of `var` was quite confusing.

In the below example, you may guess that the output the values output for both variables would be 5 but running the example we see that blockScope does indeed have the value of 5 but functionScope has the value of 0. This is because of `hoisting` which basically means any variables declared with `var` will move to the top of the function, you can think of it as the `functionScope` variable inside the `if` replacing the one declared outside.

```javascript
function bindingExample() {
  var functionScope = 5;
  let blockScope = 5;

  if (true) {
    let blockScope = 0;
    var functionScope = 0;
  }
  
  console.log(functionScope);
  console.log(blockScope);
}

bindingExample();
```

My advice is to forget about `var` and use `let` or better yet `const` instead.

## const vs let

`const` lets you define a constant binding to a value. Like `let` it is block scoped. The binding cannot be changed, unfortunatley the value can still be altered.

```javascript
  const mike = { name: "Mike McHugh" };

  mike.name = "Michael McHugh"; // Legal, no problems

  mike = {}; // Illegal, TypeError
```

I think it would be better if `const` created truly immutable values but at least it makes clear the programmer's intention.