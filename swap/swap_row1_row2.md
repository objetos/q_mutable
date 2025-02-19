---
weight: 1
title: swap(row1, row2)  
---

Swaps the contents of `row1` and `row2` in the `quadrille`.

## Example

(click to select rows, press `s` to swap, or `r` to randomize)\
{{< p5-global-iframe quadrille="true" width="525" height="525" >}}
'use strict';

let quadrille, hint;
let images = [];
let row1 = 0, row2 = 4; // Default active rows
let activeRow = 1; // Indicates which row (1 or 2) is updated on a click

function preload() {
  for (let i = 1; i <= 25; i++) {
    images.push(loadImage(`/paintings/p${i}.jpg`));
  }
}

function setup() {
  createCanvas(500, 500);
  // Create the quadrilles
  quadrille = createQuadrille(5, images);
  hint = createQuadrille(5, 1); // For drawing row hints
}

function draw() {
  background('DeepSkyBlue');
  // Draw the quadrille
  drawQuadrille(quadrille, { outlineWeight: 1 });
  // Draw hints for the selected rows
  drawQuadrille(hint, { outline: 'magenta', row: row1 });
  drawQuadrille(hint, { outline: 'cyan', row: row2 });
}

function mousePressed() {
  const row = quadrille.mouseRow;
  if (row >= 0 && row < quadrille.height) {
    // Update the active row
    activeRow === 1 ? (row1 = row) : (row2 = row);
    activeRow = activeRow === 1 ? 2 : 1; // Alternate active row
  }
}

function keyPressed() {
  if (key === 's') {
    quadrille.swap(row1, row2); // Swap the selected rows
  }
  if (key === 'r') {
    quadrille.randomize();
  }
}
{{< /p5-global-iframe >}}

{{% details title="code" open=true %}}
```js
let quadrille, hint;
let images = [];
let row1 = 0, row2 = 4; // Default active rows
let activeRow = 1; // Indicates which row (1 or 2) is updated on a click

function preload() {
  for (let i = 1; i <= 25; i++) {
    images.push(loadImage(`/paintings/p${i}.jpg`));
  }
}

function setup() {
  createCanvas(500, 500);
  // Create the quadrilles
  quadrille = createQuadrille(5, images);
  hint = createQuadrille(5, 1); // For drawing row hints
}

function draw() {
  background('DeepSkyBlue');
  // Draw the quadrille
  drawQuadrille(quadrille, { outlineWeight: 1 });
  // Draw hints for the selected rows
  drawQuadrille(hint, { outline: 'magenta', row: row1 });
  drawQuadrille(hint, { outline: 'cyan', row: row2 });
}

function mousePressed() {
  const row = quadrille.mouseRow;
  if (row >= 0 && row < quadrille.height) {
    // Update the active row
    activeRow === 1 ? (row1 = row) : (row2 = row);
    activeRow = activeRow === 1 ? 2 : 1; // Alternate active row
  }
}

function keyPressed() {
  if (key === 's') {
    quadrille.swap(row1, row2); // Swap the selected rows
  }
  if (key === 'r') {
    quadrille.randomize();
  }
}
```
{{% /details %}}

## Syntax

> `swap(row1, row2)`

## Parameters

| Param     | Description                              |
|-----------|------------------------------------------|
| `row1`    | Number: Index of the first row to swap   |
| `row2`    | Number: Index of the second row to swap  |