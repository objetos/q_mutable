---
weight: 7
title: clear(row, col, border)
---

Clears a specific cell and all connected cells **holding the same value as it** via [flood fill](https://en.wikipedia.org/wiki/Flood_fill); with `border = true`, the **rim** where the flood stops is cleared too.

## Example

(click on any cell to perform flood fill with selected border option; press any key to reset)\
{{< p5 quadrille="true" >}}
'use strict';
Quadrille.cellLength = 20;
let quadrille;
let mode;

function setup() {
  createCanvas(400, 400);
  mode = createSelect();
  mode.option('flood fill without border');
  mode.option('flood fill with border');
  mode.selected('flood fill without border');
  reset();
}

function draw() {
  background('black');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  const border = mode.value() === 'flood fill with border';
  quadrille.clear(row, col, 4, border);
}

function keyPressed() {
  reset();
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('lime')).rand(100, color('blue'));
}
{{< /p5 >}}

{{% details title="code" open=true %}}
```js
Quadrille.cellLength = 20;
let quadrille;
let mode;

function setup() {
  createCanvas(400, 400);
  mode = createSelect();
  mode.option('flood fill without border');
  mode.option('flood fill with border');
  mode.selected('flood fill without border');
  reset();
}

function draw() {
  background('black');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  const border = mode.value() === 'flood fill with border';
  quadrille.clear(row, col, 4, border);
}

function keyPressed() {
  reset();
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('lime')).rand(100, color('blue'));
}
```
{{% /details %}}

{{< callout type="info" >}}
**Connected means same value, and sameness is identity** (`===`) — see [clear(row, col, directions)]({{< ref "clear_row_col_directions" >}}). With `border = true`, the flood also clears the **rim**: the non-matching cells adjacent to the region, exactly where the expansion stops — the classic Minesweeper cascade, revealing the numbers that surround a cleared area.
{{< /callout >}}

## Syntax

> `clear(row, col, border)`

## Parameters

| Param     | Description                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| `row`     | Number: row index of the cell to start clearing [[0..height]]({{< ref "height" >}})       |
| `col`     | Number: column index of the cell to start clearing [[0..width]]({{< ref "width" >}})      |
| `border`  | Boolean: Specifies whether to include the border of the flood fill area. Default is `false` |
