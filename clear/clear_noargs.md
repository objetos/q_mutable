---
weight: 1
title: clear()
---

Clears all cells in the quadrille, setting each cell to empty (i.e., `null`).

## Example

(press `c` to clear all cells or `r` to reset)\
{{< p5-global-iframe quadrille="true" width="425" height="425" >}}
`use strict`;
Quadrille.cellLength = 20;
let quadrille;

function setup() {
  createCanvas(400, 400);
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(quadrille);
}

function keyPressed() {
  if (key === 'c') {
    quadrille.clear();
  }
  if (key === 'r') {
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('green')).rand(100, color('blue')).rand(100, color('cyan'));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.cellLength = 20;
let quadrille;

function setup() {
  createCanvas(400, 400);
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(quadrille);
}

function keyPressed() {
  if (key === 'c') {
    quadrille.clear();
  }
  if (key === 'r') {
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('green')).rand(100, color('blue')).rand(100, color('cyan'));
}
```
{{< /details >}}

## Syntax

> `clear()`