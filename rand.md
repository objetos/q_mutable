---
weight: 6
draft: false
---

# `rand()`

Use `pattern` to randomly fill (or clear if `pattern` is `null`) cells the specified number of `times`.

# Examples

(numeric keys define repetition number of `times`, other keys define `pattern`, **c** sets it as `null`)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="355" height="385" >}}
`use strict`;
Quadrille.CELL_LENGTH = 30;
let times = 5;
let pattern, patterns;
let quadrille;
let p;

function setup() {
  createCanvas(11 * Quadrille.CELL_LENGTH, 11 * Quadrille.CELL_LENGTH);
  patterns = ['👻', '✈️', null, color('cyan'), 125, '🐒', '🐍'];
  pattern = '🐒';
  quadrille = createQuadrille(11, 11, times, pattern);
  p = createP();
  p.html('mouse click: ' + (pattern === null ? 'clears ' : 'fills ')
         + times + ' time(s) with ' + pattern);
  p.style('font-size', '16px');
  p.position(10, height);
}

function draw() {
  background('yellow');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.rand(times, pattern);
}

function keyPressed() {
  +key ? times = +key : pattern = key === 'c' ? null : random(patterns);
  p.html('mouse click: ' + (pattern === null ? 'clears ' : 'fills ')
         + times + ' time(s) with ' + pattern);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 30;
let times = 5;
let pattern, patterns;
let quadrille;
let p;

function setup() {
  createCanvas(11 * Quadrille.CELL_LENGTH, 11 * Quadrille.CELL_LENGTH);
  patterns = ['👻', '✈️', null, color('cyan'), 125, '🐒', '🐍'];
  pattern = '🐒';
  quadrille = createQuadrille(11, 11, times, pattern);
  p = createP();
  p.html('mouse click: ' + (pattern === null ? 'clears ' : 'fills ')
         + times + ' time(s) with ' + pattern);
  p.style('font-size', '16px');
  p.position(10, height);
}

function draw() {
  background('yellow');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.rand(times, pattern);
}

function keyPressed() {
  +key ? times = +key : pattern = key === 'c' ? null : random(patterns);
  p.html('mouse click: ' + (pattern === null ? 'clears ' : 'fills ')
         + times + ' time(s) with ' + pattern);
}
```
{{< /details >}}

`rand()` is also exemplified in [reflect]({{< ref "reflect#example" >}}), [rotate]({{< ref "rotate#example" >}}), [transpose]({{< ref "transpose#example" >}}), [magnitude]({{< ref "magnitude#example" >}}), [ring]({{< ref "ring#example" >}}), [clear]({{< ref "clear#example" >}}), [fill]({{< ref "fill#example" >}}), [delete]({{< ref "delete#example" >}}), [insert]({{< ref "insert#example" >}}), [replace]({{< ref "replace#example" >}}), [visit_quadrille]({{< ref "visit_quadrille#examples" >}}), [width]({{< ref "width#example" >}}), [height]({{< ref "height#example" >}}) and [size]({{< ref "size#example" >}}).

# Syntax

> `rand(times, pattern = null)`

# Parameters

| parameter | description                                                                                                                                                         |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| times     | Number: number of cells to be (cleared) filled |
| pattern   | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number \| `null`: clear cells |