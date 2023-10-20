---
weight: 3
draft: false
---

# `fill()`

Fills quadrille cells in several ways: 1. Without value: as a chessboard; or, 2. With `value`: in current empty cells, a specific cell, a designated row, or a group of matching cells using [flood fill](https://en.m.wikipedia.org/wiki/Flood_fill).

# Example

(click on any cell; press 'f' to fill empty cells or 'r' to reset)\
{{< p5-global-iframe lib1="/p5.quadrille.js/docs/libs/p5.quadrille.js" width="425" height="445" >}}
`use strict`;
Quadrille.CELL_LENGTH = 20;
let quadrille, board;
let value;
let mode;

function setup() {
  createCanvas(400, 400);
  mode = createSelect();
  mode.option('chess board pattern');
  mode.option('cell');
  mode.option('row');
  mode.option('flood fill 4-directions');
  mode.option('flood fill 4-directions border');
  mode.option('flood fill 8-directions');
  mode.option('flood fill 8-directions border');
  mode.selected('cell');
  board = createQuadrille(20, 20).fill();
  reset();
  value = color('cyan');
}

function draw() {
  background('orange');
  if (mode.value() === 'chess board pattern') {
    drawQuadrille(board, { tileDisplay: 0 });
  }
  else {
    drawQuadrille(quadrille);
  }
}

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  switch(mode.value()) {
  case 'cell':
    quadrille.fill(row, col, value);
    break;
  case 'row':
    quadrille.fill(row, value);
    break;
  case 'flood fill 4-directions':
    quadrille.fill(row, col, value, 4);
    break;
  case 'flood fill 4-directions border':
    quadrille.fill(row, col, value, 4, true);
    break;
  case 'flood fill 8-directions':
    quadrille.fill(row, col, value, 8);
    break;
  case 'flood fill 8-directions border':
    quadrille.fill(row, col, value, 8, true);
    break;
  }
}

function keyPressed() {
  if (key === 'f') {
    quadrille.fill(value);
  }
  if (key === 'r') {
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('green')).rand(100, color('blue'));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 20;
let quadrille, board;
let value;
let mode;

function setup() {
  createCanvas(400, 400);
  mode = createSelect();
  mode.option('chess board pattern');
  mode.option('cell');
  mode.option('row');
  mode.option('flood fill 4-directions');
  mode.option('flood fill 4-directions border');
  mode.option('flood fill 8-directions');
  mode.option('flood fill 8-directions border');
  mode.selected('cell');
  board = createQuadrille(20, 20).fill();
  reset();
  value = color('cyan');
}

function draw() {
  background('orange');
  if (mode.value() === 'chess board pattern') {
    drawQuadrille(board, { tileDisplay: 0 });
  }
  else {
    drawQuadrille(quadrille);
  }
}

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  switch(mode.value()) {
  case 'cell':
    quadrille.fill(row, col, value);
    break;
  case 'row':
    quadrille.fill(row, value);
    break;
  case 'flood fill 4-directions':
    quadrille.fill(row, col, value, 4);
    break;
  case 'flood fill 4-directions border':
    quadrille.fill(row, col, value, 4, true);
    break;
  case 'flood fill 8-directions':
    quadrille.fill(row, col, value, 8);
    break;
  case 'flood fill 8-directions border':
    quadrille.fill(row, col, value, 8, true);
    break;
  }
}

function keyPressed() {
  if (key === 'f') {
    quadrille.fill(value);
  }
  if (key === 'r') {
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('green')).rand(100, color('blue'));
}
```
{{< /details >}}

# Syntax

> `fill()`

> `fill(value)`

> `fill(row, col, value)`

> `fill(row, value)`

> `fill(row, col, value, directions, border)`

> `fill(row, col, value, directions)`

> `fill(row, col, value, border)`

# Parameters

| parameter  | description                                                                                                                                                         |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| value      | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number \| `null`: empty cells |
| row        | Number: col number of the cell to be filled [\[0..height\]]({{< ref "height" >}})                                                                                   |
| col        | Number: row number of the cell to be filled [\[0..width\]]({{< ref "width" >}})                                                                                     |
| directions | Number: 4 or 8 directions of flood fill default is 4                                                |
| border     | Boolean: specifies whether to include the border of a filling area in flood fill default is `false` |