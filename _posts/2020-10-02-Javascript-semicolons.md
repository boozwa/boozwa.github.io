---
title: "Semicolons in JavaScript"
date: 2020-10-2T15:34:30-04:00
excerpt: "A quick set of rules to follow on Javascript semicolons"
categories:
  - programming
tags:
  - programming
  - javascript
  - syntax
share: true
---
Good reference to javascript [Semi-colons][semi-colon]. I wanted to just keep this page in my blog in case the link breaks

Semicolons in JavaScript divide the community. Some prefer to use them always, no matter what. Others like to avoid them.

After using semicolons for years, in the fall of 2017 I decided to try avoiding them as needed, and I did set up Prettier to automatically remove semicolons from my code, unless there is a particular code construct that requires them.

Now I find it natural to avoid semicolons, I think the code looks better and it’s cleaner to read.

This is all possible because JavaScript does not strictly require semicolons. When there is a place where a semicolon was needed, it adds it behind the scenes.

The process that does this is called Automatic Semicolon Insertion.

It’s important to know the rules that power semicolons, to avoid writing code that will generate bugs because does not behave like you expect.

The rules of JavaScript Automatic Semicolon Insertion
The JavaScript parser will automatically add a semicolon when, during the parsing of the source code, it finds these particular situations:

when the next line starts with code that breaks the current one (code can spawn on multiple lines)
when the next line starts with a }, closing the current block
when the end of the source code file is reached
when there is a return statement on its own line
when there is a break statement on its own line
when there is a throw statement on its own line
when there is a continue statement on its own line 

**Example 1**
```javascript
const hey = 'hey'
const you = 'hey'
const heyYou = hey + ' ' + you

['h', 'e', 'y'].forEach((letter) => console.log(letter))
```
You’ll get the error Uncaught TypeError: Cannot read property 'forEach' of undefined because based on rule 1 JavaScript tries to interpret the code as
```javascript
const hey = 'hey';
const you = 'hey';
const heyYou = hey + ' ' + you['h', 'e', 'y'].forEach((letter) => console.log(letter))
```
**Example 2**

```javascript
  // Click Event Listener drops a token in a column and checks win conditions
  for (i = 0; i < 7; i++) {
      var topRowElems = document.querySelector("#cell" + i + "6")
      topRowElems.addEventListener("click", function () {
          dropInColumn(this.id.charAt(4));
          if (rowWin() == true | columnWin() == true | diagnalWin() == true) {
              alert(getColor() + " WINS!");
              winTally();
              for (j = 0; j < 4; j++) {
                  var blah = document.getElementById("cell" + winningCells[j].x + winningCells[j].y);
                  blah.classList.add("outline");
              }
          }
          nextTurn();
      });
  }
```
**Example 3**
```javascript
 (1 + 2).toString()
 ```
 prints "3".

 ```javascript
 const a = 1
const b = 2
const c = a + b
(a + b).toString()
```
nstead raises a TypeError: b is not a function exception, because JavaScript tries to interpret it as

```javascript
const a = 1
const b = 2
const c = a + b(a + b).toString()
```

**Example 4**
Another example based on rule 4:

```javascript
(() => {
  return
  {
    color: 'white'
  }
})()
```

You’d expect the return value of this immediately-invoked function to be an object that contains the color property, but it’s not. Instead, it’s undefined, because JavaScript inserts a semicolon after return.

Instead you should put the opening bracket right after return:

```javascript
(() => {
  return {
    color: 'white'
  }
})()
```
**Example 5**
You’d think this code shows ‘0’ in an alert:

```javascript
1 + 1
-1 + 1 === 0 ? alert(0) : alert(2)
```

but it shows 2 instead, because JavaScript per rule 1 interprets it as:

```javascript
1 + 1 -1 + 1 === 0 ? alert(0) : alert(2)
```
**Conclusion**
Be careful with return statements. If you return something, add it on the same line as the return (same for break, throw, continue)

Never start a line with parentheses, those might be concatenated with the previous line to form a function call, or array element reference

[semi-colon]: https://flaviocopes.com/javascript-automatic-semicolon-insertion/#:~:text=The%20rules%20of%20JavaScript%20Automatic,can%20spawn%20on%20multiple%20lines)