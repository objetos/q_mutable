---
weight: 2
draft: false
title: shift(n, wrap)
---

Shifts the whole grid left or right. Returns this quadrille (**chainable**).

* `n > 0` shifts **left** by `n`; `n < 0` shifts **right** by `|n|`.
* With `wrap` on (default) it **wraps around**; with `wrap` off it **slides**, leaving **empty cells** behind.

## Example

(click to shift; press any key to reset)
{{< p5-global-iframe quadrille="true" width="475" height="325" >}}
'use strict';

let q;
let vertical, wrap, flip;

Quadrille.outlineWeight = 1;
Quadrille.cellLength = 30;

function setup() {
  createCanvas(450, 300);
  reset();
  // Shift controls:
  // Vertical: shift along columns (via transpose → shift → transpose)
  vertical = createCheckbox('Vertical', true);
  vertical.position(10, 10);
  vertical.style('color', '#ddd');
  // Wrap: circular rotation when ON; logical slide (empty-fill) when OFF
  wrap = createCheckbox('Wrap', true);
  wrap.position(10, 32);
  wrap.style('color', '#ddd');
  // Flip: reverses direction (left/up vs right/down)
  flip = createCheckbox('Flip', true);
  flip.position(10, 54);
  flip.style('color', '#ddd');
}

function draw() {
  background(20);
  drawQuadrille(q);
}

function mousePressed() {
  // Resolve UI to shift parameters:
  const isVertical = vertical.checked(); // shift along cols (true), rows (false)
  const shouldWrap = wrap.checked();     // wrap-around (true) vs slide (false)
  const step = flip.checked() ? -1 : 1;  // invert direction
  // Apply one-cell shift:
  // Horizontal: shift directly
  // Vertical: transpose to treat columns as rows, shift, then transpose back
  isVertical
    ? q.transpose().shift(step, shouldWrap).transpose()
    : q.shift(step, shouldWrap);
}

function keyPressed() {
  reset();
}

function reset() {
  // Random board so shift behavior is easy to see on click
  q = createQuadrille(16, 10)
    .rand(5, '🐲')
    .rand(5, '🦑')
    .rand(5, '🦜')
    .rand(5, '🐦')
    .rand(5, '🐞')
    .rand(5, '🍄');
}
{{< /p5-global-iframe >}}

{{% details title="code" open=true %}}
```js
let q;
let vertical, wrap, flip;

Quadrille.outlineWeight = 1;
Quadrille.cellLength = 30;

function setup() {
  createCanvas(450, 300);
  reset();
  // Shift controls:
  // Vertical: shift along columns (via transpose → shift → transpose)
  vertical = createCheckbox('Vertical', true);
  vertical.position(10, 10);
  vertical.style('color', '#ddd');
  // Wrap: circular rotation when ON; logical slide (empty-fill) when OFF
  wrap = createCheckbox('Wrap', true);
  wrap.position(10, 32);
  wrap.style('color', '#ddd');
  // Flip: reverses direction (left/up vs right/down)
  flip = createCheckbox('Flip', true);
  flip.position(10, 54);
  flip.style('color', '#ddd');
}

function draw() {
  background(20);
  drawQuadrille(q);
}

function mousePressed() {
  // Resolve UI to shift parameters:
  const isVertical = vertical.checked(); // shift along cols (true), rows (false)
  const shouldWrap = wrap.checked();     // wrap-around (true) vs slide (false)
  const step = flip.checked() ? -1 : 1;  // invert direction
  // Apply one-cell shift:
  // Horizontal: shift directly
  // Vertical: transpose to treat columns as rows, shift, then transpose back
  isVertical
    ? q.transpose().shift(step, shouldWrap).transpose()
    : q.shift(step, shouldWrap);
}

function keyPressed() {
  reset();
}

function reset() {
  // Random board so shift behavior is easy to see on click
  q = createQuadrille(16, 10)
    .rand(5, '🐲')
    .rand(5, '🦑')
    .rand(5, '🦜')
    .rand(5, '🐦')
    .rand(5, '🐞')
    .rand(5, '🍄');
}
```
{{% /details %}}

## Syntax

> `shift([n = 1], [wrap = true])`

## Parameters

| Param  | Description                                                                                                                                   |
| :----- | :-------------------------------------------------------------------------------------------------------------------------------------------- |
| `n`    | **Number** (default `1`). How many cells to shift. `n > 0` shifts left; `n < 0` shifts right |
| `wrap` | **Boolean** (default `true`). When on, the grid wraps around; when off, it slides and leaves empty spaces                                    |