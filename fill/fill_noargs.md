---
weight: 1
title: fill()
---

Fills all cells in the quadrille with a chessboard pattern.

## Example

(click or press any key to toggle between filling and clearing the quadrille)\
{{< p5-global-iframe quadrille="true" width="425" height="425" >}}
`use strict`;
Quadrille.cellLength = 20;
let board = true;
let quadrille;

function setup() {
  createCanvas(400, 400);
  quadrille = createQuadrille(20, 20);
  quadrille.fill();  // create a chessboard pattern
}

function draw() {
  background('black');
  drawQuadrille(quadrille, { tileDisplay: board ? 0 : Quadrille.tileDisplay });
}

function mouseClicked() {
  board = !board;
  board ? quadrille.fill() : quadrille.clear();
}

function keyPressed() {
  board = !board;
  board ? quadrille.fill() : quadrille.clear();
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.cellLength = 20;
let board = true;
let quadrille;

function setup() {
  createCanvas(400, 400);
  quadrille = createQuadrille(20, 20);
  quadrille.fill();  // create a chessboard pattern
}

function draw() {
  background('orange');
  drawQuadrille(quadrille, { tileDisplay: board ? 0 : Quadrille.tileDisplay });
}

function mouseClicked() {
  board = !board;
  board ? quadrille.fill() : quadrille.clear();
}

function keyPressed() {
  board = !board;
  board ? quadrille.fill() : quadrille.clear();
}
```
{{< /details >}}

## Syntax

> `fill()`