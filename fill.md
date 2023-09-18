---
weight: 3
draft: false
---

# `fill()`

Fills quadrille cells with given `pattern`. Either current empty cells, a given cell, a given `row`, or a set of identical cells using [flood fill](https://en.m.wikipedia.org/wiki/Flood_fill).

# Example

(click on any cell; press 'f' to fill empty cells or 'r' to reset)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="425" height="445" >}}
`use strict`;
Quadrille.CELL_LENGTH = 20;
let quadrille;
let pattern;
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
  pattern = color('cyan');
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
    quadrille.fill(row, col, pattern);
    break;
  case 'row':
    quadrille.fill(row, pattern);
    break;
  case 'flood fill 4-directions':
    quadrille.fill(row, col, pattern, 4);
    break;
  case 'flood fill 4-directions border':
    quadrille.fill(row, col, pattern, 4, true);
    break;
  case 'flood fill 8-directions':
    quadrille.fill(row, col, pattern, 8);
    break;
  case 'flood fill 8-directions border':
    quadrille.fill(row, col, pattern, 8, true);
    break;
  }
}

function keyPressed() {
  if (key === 'f') {
    quadrille.fill(pattern);
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
let quadrille;
let pattern;
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
  pattern = color('cyan');
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
    quadrille.fill(row, col, pattern);
    break;
  case 'row':
    quadrille.fill(row, pattern);
    break;
  case 'flood fill 4-directions':
    quadrille.fill(row, col, pattern, 4);
    break;
  case 'flood fill 4-directions border':
    quadrille.fill(row, col, pattern, 4, true);
    break;
  case 'flood fill 8-directions':
    quadrille.fill(row, col, pattern, 8);
    break;
  case 'flood fill 8-directions border':
    quadrille.fill(row, col, pattern, 8, true);
    break;
  }
}

function keyPressed() {
  if (key === 'f') {
    quadrille.fill(pattern);
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

> `fill(pattern)`

> `fill(row, col, pattern)`

> `fill(row, pattern)`

> `fill(row, col, pattern, directions, border)`

> `fill(row, col, pattern, directions)`

> `fill(row, col, pattern, border)`

# Parameters

| parameter  | description                                                                                                                                                         |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| pattern    | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number \| `null`: empty cells |
| row        | Number: col number of the cell to be filled [\[0..height\]]({{< ref "height" >}})                                                                                   |
| col        | Number: row number of the cell to be filled [\[0..width\]]({{< ref "width" >}})                                                                                     |
| directions | Number: 4 or 8 directions of flood fill default is 4                                                |
| border     | Boolean: specifies whether to include the border of a filling area in flood fill default is `false` |