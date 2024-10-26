---
weight: 1
title: fill()
---

Fills all cells in the quadrille with a chessboard pattern by default (when no `value` is provided).

## Example

(press `f` to fill all empty cells with the default pattern or `r` to reset)\
{{< p5-global-iframe quadrille="true" width="425" height="445" >}}
`use strict`;
Quadrille.cellLength = 20;
let quadrille, board;

function setup() {
  createCanvas(400, 400);
  board = createQuadrille(20, 20).fill();  // create a chessboard pattern
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(board, { tileDisplay: 0 });
}

function keyPressed() {
  if (key === 'f') {
    quadrille.fill();
  }
  if (key === 'r') {
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(20, 20);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.cellLength = 20;
let quadrille, board;

function setup() {
  createCanvas(400, 400);
  board = createQuadrille(20, 20).fill();  // create a chessboard pattern
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(board, { tileDisplay: 0 });
}

function keyPressed() {
  if (key === 'f') {
    quadrille.fill();
  }
  if (key === 'r') {
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(20, 20);
}
```
{{< /details >}}

## Syntax

> `fill()`