---
weight: 3
title: fill(predicate, value)
---

Fills cells matching a predicate condition with the specified `value`.

## Example

(move the mouse to fill empty cells in the current row with `🐉`; click to reset)  
{{< p5 quadrille="true" >}}
'use strict';

Quadrille.cellLength = 40;
let quadrille;

function setup() {
  createCanvas(400, 400);
  reset();
}

function draw() {
  background('black');
  drawQuadrille(quadrille);
}

function mouseMoved() {
  quadrille.fill(({ row, col, value }) => row === quadrille.mouseRow && value === null, '🐉');
}

function mouseClicked() {
  reset();
}

function reset() {
  quadrille = createQuadrille(10, 10, 15, color('purple'));
  quadrille.rand(15, color('orange')).rand(15, color('yellow'));
}
{{< /p5 >}}

{{% details title="code" open=true %}}

```js
Quadrille.cellLength = 40;
let quadrille;

function setup() {
  createCanvas(400, 400);
  reset();
}

function draw() {
  background('black');
  drawQuadrille(quadrille);
}

function mouseMoved() {
  quadrille.fill(({ row, col, value }) => row === quadrille.mouseRow && value === null, '🐉');
}

function mouseClicked() {
  reset();
}

function reset() {
  quadrille = createQuadrille(10, 10, 15, color('purple'));
  quadrille.rand(15, color('orange')).rand(15, color('yellow'));
}
```

{{% /details %}}

## Syntax

> `fill(predicate, value)`

## Parameters

| Param       | Description                                                                               |
| ----------- | ----------------------------------------------------------------------------------------- |
| `predicate` | Function: A predicate function `({ row, col, value }) => boolean` selecting cells to fill |
| `value`[^1] | Any: A valid JavaScript value                                                             |

[^1]: A plain function `value` is **stored, not called** — it becomes a per-cell display routine `({ row, col, options }) => { ... }` (see [`options`]({{< relref display_fns >}})). To have a function **evaluated per cell** at fill time — a fresh object or a varied tile per cell — tag it: `Quadrille.factory(({ row, col }) => new Object(...))`.
