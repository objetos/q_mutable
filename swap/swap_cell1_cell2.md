---
weight: 1
title: swap(row1, col1, row2, col2)
---

Swaps the contents of the cell at `(row1, col1)` with the cell at `(row2, col2)` in the `quadrille`.

## Example

(click to select cells, press `s` to swap, or `r` to randomize)\
{{< p5-global-iframe quadrille="true" width="525" height="525" >}}
'use strict'

let quadrille, hint;
let images = [];
let cell1 = [0, 0], cell2 = [4, 4]; // Start with two active cells
let activeCell = 1; // Indicates which cell (1 or 2) moves on a click

function preload() {
  for (let i = 1; i <= 25; i++) {
    images.push(loadImage(`/paintings/p${i}.jpg`));
  }
}

function setup() {
  createCanvas(500, 500);
  // Create the quadrilles
  quadrille = createQuadrille(5, images);
  hint = createQuadrille(1, 1);
}

function draw() {
  background('DeepSkyBlue');
  // Draw the quadrille
  drawQuadrille(quadrille, { outlineWeight: 1 });
  // Draw hints
  drawQuadrille(hint, { outline: 'magenta', row: cell1[0], col: cell1[1] });
  drawQuadrille(hint, { outline: 'cyan', row: cell2[0], col: cell2[1] });
}

function mousePressed() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  if (row >= 0 && row < quadrille.height && col >= 0 && col < quadrille.width) {
    // Update active cell
    activeCell === 1 ? (cell1 = [row, col]) : (cell2 = [row, col]);
    activeCell = activeCell === 1 ? 2 : 1; // Alternate active cell
  }
}

function keyPressed() {
  if (key === 's') {
    const [row1, col1] = cell1;
    const [row2, col2] = cell2;
    quadrille.swap(row1, col1, row2, col2);
  }
  if (key === 'r') {
    quadrille.randomize();
  }
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
let quadrille, hint;
let images = [];
let cell1 = [0, 0], cell2 = [4, 4]; // Start with two active cells
let activeCell = 1; // Indicates which cell (1 or 2) moves on a click

function preload() {
  for (let i = 1; i <= 25; i++) {
    images.push(loadImage(`/paintings/p${i}.jpg`));
  }
}

function setup() {
  createCanvas(500, 500);
  // Create the quadrilles
  quadrille = createQuadrille(5, images);
  hint = createQuadrille(1, 1);
}

function draw() {
  background('DeepSkyBlue');
  // Draw the quadrille
  drawQuadrille(quadrille, { outlineWeight: 1 });
  // Draw hints
  drawQuadrille(hint, { outline: 'magenta', row: cell1[0], col: cell1[1] });
  drawQuadrille(hint, { outline: 'cyan', row: cell2[0], col: cell2[1] });
}

function mousePressed() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  if (row >= 0 && row < quadrille.height && col >= 0 && col < quadrille.width) {
    // Update active cell
    activeCell === 1 ? (cell1 = [row, col]) : (cell2 = [row, col]);
    activeCell = activeCell === 1 ? 2 : 1; // Alternate active cell
  }
}

function keyPressed() {
  if (key === 's') {
    const [row1, col1] = cell1;
    const [row2, col2] = cell2;
    quadrille.swap(row1, col1, row2, col2);
  }
  if (key === 'r') {
    quadrille.randomize();
  }
}
```
{{< /details >}}

## Syntax

> `swap(row1, col1, row2, col2)`

## Parameters

| Parameter | Description                            |
|-----------|----------------------------------------|
| row1      | Number: Row index of the first cell    |
| col1      | Number: Column index of the first cell |
| row2      | Number: Row index of the second cell   |
| col2      | Number: Column index of the second cell|