---
weight: 1
draft: false
---

# `delete()`

Deletes a row from the quadrille.

# Example

(click on any cell; press any key to reset)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="425" height="425" >}}
`use strict`;
Quadrille.CELL_LENGTH = 20;
let quadrille;

function setup() {
  createCanvas(400, 400);
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.delete(quadrille.mouseRow);
}

function keyPressed() {
  reset();
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('green')).rand(100, color('blue')).
            rand(100, color('cyan'));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 20;
let quadrille;

function setup() {
  createCanvas(400, 400);
  reset();
}

function draw() {
  background('orange');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.delete(quadrille.mouseRow);
}

function keyPressed() {
  reset();
}

function reset() {
  quadrille = createQuadrille(20, 20, 100, color('red'));
  quadrille.rand(100, color('green')).rand(100, color('blue')).
            rand(100, color('cyan'));
}
```
{{< /details >}}

# Syntax

> `delete(row)`

# Parameters

| parameter | description                                                               |
|-----------|---------------------------------------------------------------------------|
| row       | Number: number of row to be deleted [\[0..height\]]({{< ref "height" >}}) |