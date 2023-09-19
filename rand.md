---
weight: 6
draft: false
---

# `rand()`

Randomly (clear or) fill quadrille cells with `pattern` the specified number of `times`.

# Examples

(mouse clicked or key pressed fills / clears `quadrille`\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="355" height="415" >}}
`use strict`;
Quadrille.CELL_LENGTH = 30;
let mode;
let times;
let patterns;
let quadrille;

function setup() {
  createCanvas(11 * Quadrille.CELL_LENGTH, 11 * Quadrille.CELL_LENGTH);
  // modes
  // false -> fill
  // true -> clear
  mode = createCheckbox('clear', false);
  times = createSlider(1, 5, 2, 1);
  patterns = ['👻', '✈️', color('cyan'), 125, '🐒', '🐍'];
  quadrille = createQuadrille(11, 11, times.value(), random(patterns)); 
}

function draw() {
  background('yellow');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.rand(times.value(), mode.checked() ? null : random(patterns));
}

function keyPressed() {
  quadrille.rand(times.value(), mode.checked() ? null : random(patterns));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 30;
let mode;
let times;
let patterns;
let quadrille;

function setup() {
  createCanvas(11 * Quadrille.CELL_LENGTH, 11 * Quadrille.CELL_LENGTH);
  // modes
  // false -> fill
  // true -> clear
  mode = createCheckbox('clear', false);
  times = createSlider(1, 5, 2, 1);
  patterns = ['👻', '✈️', color('cyan'), 125, '🐒', '🐍'];
  quadrille = createQuadrille(11, 11, times.value(), random(patterns)); 
}

function draw() {
  background('yellow');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.rand(times.value(), mode.checked() ? null : random(patterns));
}

function keyPressed() {
  quadrille.rand(times.value(), mode.checked() ? null : random(patterns));
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