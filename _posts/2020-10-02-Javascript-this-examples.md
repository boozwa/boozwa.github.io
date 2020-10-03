---
title: "Javascript Function with *this* keyword"
date: 2020-10-3T15:34:30-04:00
excerpt: "Good reference to the ... syntax for a function within an object literal"
categories:
  - programming
tags:
  - programming
  - javascript
  - syntax
  - functions
  - this keyword
share: true
---
Good reference to javascript function using *this* keyword in an obect literal. Came from a [webpage][web-page] on different ways to write a js function. 

**Example 1**

Function Shorthand methods:
Shorthand method definition can be used in a method declaration on object literals and ES6 classes. We can define them using a function name, followed by a list of parameters in a pair of parenthesis (para1, ..., paramN) and a pair of curly braces { ... } that delimits the body statements.

The following example uses shorthand method definition in an object literal:
Note the ... syntax. Kinda cool!

```javascript
const fruits = {  
  items: [],
  add(...items) {
    this.items.push(...items);
  },
  get(index) {
    return this.items[index];
  }
};
fruits.add('mango', 'banana', 'guava');  
fruits.get(1); // banana
```
add() and get() methods in fruits object are defined using short method definition. These methods are called as usual: fruits.add(...) and fruits.get(...).


[web-page]: https://dev.to/jamal_uddin95/different-type-of-function-in-javascript-364l
