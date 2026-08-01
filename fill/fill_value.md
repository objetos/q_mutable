---
weight: 3
title: fill(value)
---

Fills all **empty** cells in the quadrille with the specified `value` — filled cells are never overwritten (to re-value those, use [replace(value)]({{< ref "replace_value" >}}); to start over, [clear]({{< ref "clear" >}}) first). Returns the quadrille (**chainable**).

## Example

(click or press a key to toggle between filling empty cells and resetting to random colors)\
{{< p5 quadrille="true" >}}
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
{{< /p5 >}}

{{% details title="code" open=true %}}
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
{{% /details %}}

{{< callout type="info" >}}
Empty cells appear black because the background is set to black (`background(0)`), while the fill color is white (`fill(255)`).
{{< /callout >}}

{{< callout type="info" >}}
**One value, one instance.** A non-factory `value` is stored **as-is in every cell**: all cells filled by the call share the same instance. That single fact powers two idioms elsewhere in the API — strict [search]({{< ref "search" >}}) matches across cells (`===`), and [flood fill]({{< ref "fill_row_col_value_directions" >}})/[flood clear]({{< ref "clear_row_col_directions" >}}) treat them as one connected region, since the flood matches the start cell's value by identity. Per-cell instances instead — e.g. a fresh `color('green')` per cell via `Quadrille.factory` — would strict-match nothing and flood nowhere.
{{< /callout >}}

## Syntax

> `fill(value)`

## Parameters

| Param     | Description                                                                                                                         |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------|
| `value`[^1] | Any: A valid JavaScript value                                                        |

[^1]: A plain function `value` is **stored, not called** — it becomes a per-cell display routine `({ row, col, options }) => { ... }` (see [`options`]({{< relref display_fns >}})). To have a function **evaluated per cell** at fill time — a fresh object or a varied tile per cell — tag it: `Quadrille.factory(({ row, col }) => new Object(...))`.