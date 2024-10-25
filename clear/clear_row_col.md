---
weight: 2
title: clear(row, col)
---

Clears a specific cell in the quadrille, setting it to empty (i.e., `null`).

## Example

(click on any cell to clear it; press `r` to reset)\
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

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  quadrille.clear(row, col);
}

function keyPressed() {
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

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  quadrille.clear(row, col);
}

function keyPressed() {
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

> `clear(row, col)`

## Parameters

| parameter | description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| row       | Number: row number of the cell to clear [\[0..height\]]({{< ref "height" >}})  |
| col       | Number: column number of the cell to clear [\[0..width\]]({{< ref "width" >}}) |