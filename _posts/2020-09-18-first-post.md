---
title: "First Post!"
date: 2020-09-18T15:34:30-04:00
excerpt: "Yep... the first one"
categories:
  - blog
tags:
  - Generic Posts
share: true
---

This is my first post in my github-pages blog. It primarily uses Jekyll which seems like a neat static site generator. 

Here is a javascript code snippit from my connect 4 web app. 

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

Check out this [YelpCamp][yelp-camp] page that I used as reference for my blog.

[yelp-camp]: https://zouboyun.github.io/YelpCamp/