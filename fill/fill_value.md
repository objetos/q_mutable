---
weight: 3
title: fill(value)
---

Fills all empty cells in the quadrille with the specified `value`.

## Example

(click or press a key to toggle between filling empty cells and resetting to random colors)\
{{< p5-global-iframe quadrille="true" width="425" height="425" >}}
'use strict';
Quadrille.cellLength = 20;
let quadrille;
let filled = false;

function setup() {
  createCanvas(400, 400);
  reset();
}

function draw() {
  background(0);
  drawQuadrille(quadrille);
}

function mouseClicked() {
  filled = !filled;
  filled ? quadrille.fill(255) : reset();
}

function keyPressed() {
  filled = !filled;
  filled ? quadrille.fill(255) : reset();
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('lime')).rand(100, color('blue'));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.cellLength = 20;
let quadrille;
let filled = false;

function setup() {
  createCanvas(400, 400);
  reset();
}

function draw() {
  background(0);
  drawQuadrille(quadrille);
}

function mouseClicked() {
  filled = !filled;
  filled ? quadrille.fill(255) : reset();
}

function keyPressed() {
  filled = !filled;
  filled ? quadrille.fill(255) : reset();
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('lime')).rand(100, color('blue'));
}
```
{{< /details >}}

{{< callout type="info" >}}
**Observation:** Empty cells appear black because the background is set to black (`background(0)`), while the fill color is white (`fill(255)`).
{{< /callout >}}

## Syntax

> `fill(value)`

## Parameters

| parameter | description                                                                                                                         |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------|
| value     | Any: The value to fill all empty cells with. Can be a [p5.Color](https://p5js.org/reference/#/p5.Color), image, string, number, etc.|