---
bookCollapseSection: true
title: "rand(args)"
weight: 6
---

Use `value` to randomly fill (or clear if `value` is `null`) cells the specified number of `times`.

# Examples

(numeric keys define `times` while others define `value`, **c** sets it as `null`)\
{{< p5-global-iframe quadrille="true" width="385" height="415" >}}
'use strict';
Quadrille.cellLength = 30;
let times = 5;
let value, values;
let quadrille;
let p;

function setup() {
  createCanvas(12 * Quadrille.cellLength, 12 * Quadrille.cellLength);
  values = ['👻', '✈️', null, color('cyan'), 125, '🐒', '🐍'];
  value = '🐒';
  quadrille = createQuadrille(12, 12, times, value);
  p = createP();
  p.html('mouse click: ' + (value === null ? 'clears ' + times + ' time(s)'
         : 'fills ' + times + ' time(s) with ' + value));
  p.style('font-size', '16px');
  p.position(10, height);
}

function draw() {
  background('yellow');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.rand(times, value);
}

function keyPressed() {
  +key ? times = +key : value = key === 'c' ? null : random(values);
  p.html('mouse click: ' + (value === null ? 'clears ' + times + ' time(s)'
         : 'fills ' + times + ' time(s) with ' + value));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.cellLength = 30;
let times = 5;
let value, values;
let quadrille;
let p;

function setup() {
  createCanvas(12 * Quadrille.cellLength, 12 * Quadrille.cellLength);
  values = ['👻', '✈️', null, color('cyan'), 125, '🐒', '🐍'];
  value = '🐒';
  quadrille = createQuadrille(12, 12, times, value);
  p = createP();
  p.html('mouse click: ' + (value === null ? 'clears ' + times + ' time(s)'
         : 'fills ' + times + ' time(s) with ' + value));
  p.style('font-size', '16px');
  p.position(10, height);
}

function draw() {
  background('yellow');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.rand(times, value);
}

function keyPressed() {
  +key ? times = +key : value = key === 'c' ? null : random(values);
  p.html('mouse click: ' + (value === null ? 'clears ' + times + ' time(s)'
         : 'fills ' + times + ' time(s) with ' + value));
}
```
{{< /details >}}

`rand()` is also exemplified in [reflect]({{< ref "reflect#example" >}}), [rotate]({{< ref "rotate#example" >}}), [transpose]({{< ref "transpose#example" >}}), [magnitude]({{< ref "magnitude#example" >}}), [ring]({{< ref "ring#example" >}}), [clear]({{< ref "clear#example" >}}), [fill]({{< ref "fill#example" >}}), [delete]({{< ref "delete#example" >}}), [insert]({{< ref "insert#example" >}}), [replace]({{< ref "replace#example" >}}), [visit_quadrille]({{< ref "visit_quadrille#examples" >}}), [width]({{< ref "width#example" >}}), [height]({{< ref "height#example" >}}) and [size]({{< ref "size#example" >}}).

## Syntax

> `rand(times, value = null)`

## Parameters

| parameter | description                                                                                                                                                         |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| times     | Number: number of cells to be (cleared) filled |
| value     | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number \| `null`: clear cells |