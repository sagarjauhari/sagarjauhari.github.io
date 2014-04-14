---
layout: post
title: "A-Maze: Building computer generated mazes"
modified: 2014-04-13 21:18:10 -0400
category: code
tags: [python]
image:
  feature: maze-0.jpg
  credit: chrstphre campbell
  creditlink: https://www.flickr.com/photos/chrstphre/4974283829/in/photostream/
comments:
share:
---
Recently came across an [article](http://mazeworks.com/mazegen/mazetut/index.htm) talking about building a *perfect* maze. They use a simple DFS algorithm:

> 1) Start at a random cell in the grid.

> 2) Look for a random neighbor cell you haven’t been to yet.

> 3) If you find one, move there, knocking down the wall between the cells. If you don’t find one, back up to the previous cell.

> 4) Repeat steps 2 and 3 until you’ve been to every cell in the grid.

I wanted to create something like this with python’s [PIL](http://python-imaging.github.io/). Today I stumbled upon [this](http://www.janthor.com/maze/index.html) article on HackerNews in which the author has rendered several mazes using python. Would love to try out the scripts he has shared.
