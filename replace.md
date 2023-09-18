---
weight: 4
draft: false
---

# `replace()`

Either replaces non empty cells with `pattern`, or `pattern1` filled cells with `pattern2`.

# Examples

(click on any cell; press 'r' to replace filled cells or other key to reset)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="425" height="425" >}}
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
  const pattern1 = quadrille.read(quadrille.mouseRow, quadrille.mouseCol);
  quadrille.replace(pattern1, cyan);
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
  const pattern1 = quadrille.read(quadrille.mouseRow, quadrille.mouseCol);
  quadrille.replace(pattern1, cyan);
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

> `replace(pattern)`

> `replace(pattern1, pattern2)`

# Parameters

| parameter | description                                                                                                                                                        |
|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| pattern1  | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number |
| pattern2  | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number |