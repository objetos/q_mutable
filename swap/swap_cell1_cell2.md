---
weight: 1
title: swap(row1, col1, row2, col2)
---

Swaps the contents of the cell at `(row1, col1)` with the cell at `(row2, col2)` in the `quadrille`.

## Example

(click canvas and press any key to randomize `quadrille`)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js@2.2.0/p5.quadrille.js" width="525" height="540" >}}
'use strict'
let quadrille, hint;
let images = [];
let rowSelect1, colSelect1, rowSelect2, colSelect2, swapButton;

function preload() {
  for (let i = 1; i <= 25; i++) {
    images.push(loadImage(`/paintings/p${i}.jpg`));
  }
}

function setup() {
  createCanvas(500, 500);
  // Initialize the quadrille
  quadrille = createQuadrille(5, 5);
  visitQuadrille(quadrille, (r, c) => quadrille.fill(r, c, images[r * 5 + c]));
  hint = createQuadrille(1, 1);
  // Create row and column select elements for the first cell
  rowSelect1 = createSelect();
  rowSelect1.position(10, height + 10);
  colSelect1 = createSelect();
  colSelect1.position(60, height + 10);
  // Create row and column select elements for the second cell
  rowSelect2 = createSelect();
  rowSelect2.position(120, height + 10);
  colSelect2 = createSelect();
  colSelect2.position(170, height + 10);
  // Populate the selects with options
  for (let i = 0; i < quadrille.height; i++) {
    rowSelect1.option(i);
    rowSelect2.option(i);
  }
  for (let i = 0; i < quadrille.width; i++) {
    colSelect1.option(i);
    colSelect2.option(i);
  }
  // Pre-select last row and column for the second cell
  rowSelect2.selected(quadrille.height - 1);
  colSelect2.selected(quadrille.width - 1);
  // Create a button to swap the cells
  swapButton = createButton('Swap Cells');
  swapButton.position(230, height + 10);
  swapButton.mousePressed(() => {
    const row1 = int(rowSelect1.value());
    const col1 = int(colSelect1.value());
    const row2 = int(rowSelect2.value());
    const col2 = int(colSelect2.value());
    // Swap the selected cells
    quadrille.swap(row1, col1, row2, col2);
  });
}

function draw() {
  background('DeepSkyBlue');
  drawQuadrille(quadrille, { outline: 'magenta' });
  drawQuadrille(hint, { outline: 'lime',
                        row: int(rowSelect1.value()),
                        col: int(colSelect1.value()) });
  drawQuadrille(hint, { outline: 'lime',
                        row: int(rowSelect2.value()),
                        col: int(colSelect2.value()) });
}

function keyPressed() {
  quadrille.randomize();
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
let quadrille, hint;
let images = [];
let rowSelect1, colSelect1, rowSelect2, colSelect2, swapButton;

function preload() {
  for (let i = 1; i <= 25; i++) {
    images.push(loadImage(`/paintings/p${i}.jpg`));
  }
}

function setup() {
  createCanvas(500, 500);
  // Initialize the quadrille
  quadrille = createQuadrille(5, 5);
  visitQuadrille(quadrille, (r, c) => quadrille.fill(r, c, images[r * 5 + c]));
  hint = createQuadrille(1, 1);
  // Create row and column select elements for the first cell
  rowSelect1 = createSelect();
  rowSelect1.position(10, height + 10);
  colSelect1 = createSelect();
  colSelect1.position(60, height + 10);
  // Create row and column select elements for the second cell
  rowSelect2 = createSelect();
  rowSelect2.position(120, height + 10);
  colSelect2 = createSelect();
  colSelect2.position(170, height + 10);
  // Populate the selects with options
  for (let i = 0; i < quadrille.height; i++) {
    rowSelect1.option(i);
    rowSelect2.option(i);
  }
  for (let i = 0; i < quadrille.width; i++) {
    colSelect1.option(i);
    colSelect2.option(i);
  }
  // Pre-select last row and column for the second cell
  rowSelect2.selected(quadrille.height - 1);
  colSelect2.selected(quadrille.width - 1);
  // Create a button to swap the cells
  swapButton = createButton('Swap Cells');
  swapButton.position(230, height + 10);
  swapButton.mousePressed(() => {
    const row1 = int(rowSelect1.value());
    const col1 = int(colSelect1.value());
    const row2 = int(rowSelect2.value());
    const col2 = int(colSelect2.value());
    // Swap the selected cells
    quadrille.swap(row1, col1, row2, col2);
  });
}

function draw() {
  background('DeepSkyBlue');
  drawQuadrille(quadrille, { outline: 'magenta' });
  drawQuadrille(hint, { outline: 'lime',
                        row: int(rowSelect1.value()),
                        col: int(colSelect1.value()) });
  drawQuadrille(hint, { outline: 'lime',
                        row: int(rowSelect2.value()),
                        col: int(colSelect2.value()) });
}

function keyPressed() {
  quadrille.randomize();
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