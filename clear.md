---
weight: 2
draft: false
---

# `clear()`

Clears quadrille cells (i.e., sets cells to `null`). Either a given cell, a given `row`,  a set of identical cells using [flood fill](https://en.m.wikipedia.org/wiki/Flood_fill) or all cells.

# Examples

{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="425" height="465" >}}
`use strict`;
Quadrille.CELL_LENGTH = 20;
let quadrille;
let mode;

function setup() {
  createCanvas(400, 400);
  mode = createSelect();
  //mode.position(10, 10);
  mode.option('cell');
  mode.option('row');
  mode.option('flood fill 4-directions');
  mode.option('flood fill 8-directions');
  mode.selected('cell');
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  switch(mode.value()) {
  case 'cell':
    quadrille.clear(row, col);
    break;
  case 'row':
    quadrille.clear(row);
    break;
  case 'flood fill 4-directions':
    quadrille.clear(row, col, 4);
    break;
  case 'flood fill 8-directions':
    quadrille.clear(row, col, 8);
    break;
  }
}

function keyPressed() {
  
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(200, color('green')).rand(300, color('blue')).rand(400, color('cyan'));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
let quadrille;

function setup() {
  createCanvas(4 * Quadrille.CELL_LENGTH, 4 * Quadrille.CELL_LENGTH);
  quadrille = createQuadrille(4, 4, 3, '🚀');
  quadrille.rand(7, '🐒');
}

function draw() {
  background('orange');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.reflect();  
}

function keyPressed() {
  quadrille.reflect();
}
```
{{< /details >}}

# Syntax

> `clear()`

> `clear(row)`

> `clear(row, col)`

> `clear(row, col, directions)`

> `clear(row, col, border)`

> `clear(row, col, directions, border)`

# Parameters

| parameter  | description                                                                                          |
|------------|------------------------------------------------------------------------------------------------------|
| row        | Number: number of the row to be cleared [\[0..height\]]({{< ref "height" >}})                        |
| col        | Number: row number of the cell to be filled [\[0..width\]]({{< ref "width" >}})                      |
| directions | Number: 4 or 8 directions of flood fill default is 4                                                 |
| border     | Boolean: specifies whether to include the border of a clearing area in flood fill default is `false` |