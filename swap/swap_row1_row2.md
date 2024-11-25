---
weight: 1
title: swap(row1, row2)  
---

Swaps the contents of `row1` and `row2` in the `quadrille`.

## Example

(click canvas and press any key to randomize `quadrille`)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js@2.2.0/p5.quadrille.js" width="525" height="540" >}}
'use strict'
let quadrille, hint;
let images = [];
let rowSelect1, rowSelect2, swapButton;

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
  hint = createQuadrille(5, 1);
  // Create row select elements
  rowSelect1 = createSelect();
  rowSelect1.position(10, height + 10);
  rowSelect2 = createSelect();
  rowSelect2.position(60, height + 10);
  // Populate the selects with row options
  for (let i = 0; i < quadrille.height; i++) {
    rowSelect1.option(i);
    rowSelect2.option(i);
  }
  rowSelect2.selected(quadrille.height - 1);
  // Create a button to swap the rows
  swapButton = createButton('Swap Rows');
  swapButton.position(110, height + 10);
  swapButton.mousePressed(() => {
    const row1 = int(rowSelect1.value());
    const row2 = int(rowSelect2.value());
    quadrille.swap(row1, row2); // Swap the selected rows
  });
}

function draw() {
  background('DeepSkyBlue');
  drawQuadrille(quadrille, { outline: 'magenta' });
  drawQuadrille(hint, { outline: 'lime', row: int(rowSelect1.value()) });
  drawQuadrille(hint, { outline: 'lime', row: int(rowSelect2.value()) });
}

function keyPressed() {
  quadrille.randomize();
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
let quadrille, hint;
let images = [];
let rowSelect1, rowSelect2, swapButton;

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
  hint = createQuadrille(5, 1);
  // Create row select elements
  rowSelect1 = createSelect();
  rowSelect1.position(10, height + 10);
  rowSelect2 = createSelect();
  rowSelect2.position(60, height + 10);
  // Populate the selects with row options
  for (let i = 0; i < quadrille.height; i++) {
    rowSelect1.option(i);
    rowSelect2.option(i);
  }
  rowSelect2.selected(quadrille.height - 1);
  // Create a button to swap the rows
  swapButton = createButton('Swap Rows');
  swapButton.position(110, height + 10);
  swapButton.mousePressed(() => {
    const row1 = int(rowSelect1.value());
    const row2 = int(rowSelect2.value());
    quadrille.swap(row1, row2); // Swap the selected rows
  });
}

function draw() {
  background('DeepSkyBlue');
  drawQuadrille(quadrille, { outline: 'magenta' });
  drawQuadrille(hint, { outline: 'lime', row: int(rowSelect1.value()) });
  drawQuadrille(hint, { outline: 'lime', row: int(rowSelect2.value()) });
}

function keyPressed() {
  quadrille.randomize();
}
```
{{< /details >}}

## Syntax

> `swap(row1, row2)`

## Parameters

| Parameter | Description                              |
|-----------|------------------------------------------|
| row1      | Number: Index of the first row to swap   |
| row2      | Number: Index of the second row to swap  |