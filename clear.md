---
weight: 2
draft: false
---

# `clear()`

Clears quadrille cells (i.e., sets cells to `null`). Either all cells, a given cell, a given `row` or a set of identical cells using [flood fill](https://en.m.wikipedia.org/wiki/Flood_fill) or all cells.

# Example

(click on any cell; press 'c' to clear all cells or 'r' to reset)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="425" height="445" >}}
`use strict`;
Quadrille.CELL_LENGTH = 20;
let quadrille;
let mode;

function setup() {
  createCanvas(400, 400);
  mode = createSelect();
  mode.option('cell');
  mode.option('row');
  mode.option('flood fill 4-directions');
  mode.option('flood fill 4-directions border');
  mode.option('flood fill 8-directions');
  mode.option('flood fill 8-directions border');
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
  case 'flood fill 4-directions border':
    quadrille.clear(row, col, 4, true);
    break;
  case 'flood fill 8-directions':
    quadrille.clear(row, col, 8);
    break;
  case 'flood fill 8-directions border':
    quadrille.clear(row, col, 8, true);
    break;
  }
}

function keyPressed() {
  if (key === 'c') {
    quadrille.clear();
  }
  if (key === 'r'){
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('green')).rand(100, color('blue')).
            rand(100, color('cyan'));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 20;
let quadrille;
let mode;

function setup() {
  createCanvas(400, 400);
  mode = createSelect();
  mode.option('cell');
  mode.option('row');
  mode.option('flood fill 4-directions');
  mode.option('flood fill 4-directions border');
  mode.option('flood fill 8-directions');
  mode.option('flood fill 8-directions border');
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
  case 'flood fill 4-directions border':
    quadrille.clear(row, col, 4, true);
    break;
  case 'flood fill 8-directions':
    quadrille.clear(row, col, 8);
    break;
  case 'flood fill 8-directions border':
    quadrille.clear(row, col, 8, true);
    break;
  }
}

function keyPressed() {
  if (key === 'c') {
    quadrille.clear();
  }
  if (key === 'r'){
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('green')).rand(100, color('blue')).
            rand(100, color('cyan'));
}
```
{{< /details >}}

# Syntax

> `clear()`

> `clear(row, col)`

> `clear(row)`

> `clear(row, col, directions, border)`

> `clear(row, col, directions)`

> `clear(row, col, border)`

# Parameters

| parameter  | description                                                                                          |
|------------|------------------------------------------------------------------------------------------------------|
| row        | Number: number of the row to be cleared [\[0..height\]]({{< ref "height" >}})                        |
| col        | Number: row number of the cell to be filled [\[0..width\]]({{< ref "width" >}})                      |
| directions | Number: 4 or 8 directions of flood fill default is 4                                                 |
| border     | Boolean: specifies whether to include the border of a clearing area in flood fill default is `false` |