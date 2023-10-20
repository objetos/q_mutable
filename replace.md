---
weight: 4
draft: false
---

# `replace()`

Either replaces non empty cells with `value`, or `value1` filled cells with `value2`.

# Examples

(click on any cell; press 'r' to replace filled cells or other key to reset)\
{{< p5-global-iframe lib1="/p5.quadrille.js/docs/libs/p5.quadrille.js" width="425" height="425" >}}
`use strict`;
Quadrille.CELL_LENGTH = 40;
let quadrille;
let red, green, blue, cyan;

function setup() {
  createCanvas(400, 400);
  red = color('red');
  green = color('green');
  blue = color('blue');
  cyan = color('cyan');
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  const value1 = quadrille.read(quadrille.mouseRow, quadrille.mouseCol);
  quadrille.replace(value1, cyan);
}

function keyPressed() {
  if (key === 'r') {
    quadrille.replace(cyan);
  }
  else {
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(10, 10, 25, red).rand(25, green).rand(25, blue);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 40;
let quadrille;
let red, green, blue, cyan;

function setup() {
  createCanvas(400, 400);
  red = color('red');
  green = color('green');
  blue = color('blue');
  cyan = color('cyan');
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  const value1 = quadrille.read(quadrille.mouseRow, quadrille.mouseCol);
  quadrille.replace(value1, cyan);
}

function keyPressed() {
  if (key === 'r') {
    quadrille.replace(cyan);
  }
  else {
    reset();
  }
}

function reset() {
  quadrille = createQuadrille(10, 10, 25, red).rand(25, green).rand(25, blue);
}
```
{{< /details >}}

# Syntax

> `replace(value)`

> `replace(value1, value2)`

# Parameters

| parameter | description                                                                                                                                                        |
|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| value   | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number |
| value1  | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number |
| value2  | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number |