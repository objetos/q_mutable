---
weight: 5
draft: false
---

# `insert()`

Inserts an empty row into the quadrille.

# Example

(click any row; press any key to reset)\
{{< p5-global-iframe quadrille="true" width="425" height="425" >}}
`use strict`;
Quadrille.cellLength = 20;
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
  if (quadrille.height < 20) {
    quadrille.insert(quadrille.mouseRow);
  }
}

function keyPressed() {
  reset();
}

function reset() {
  quadrille = createQuadrille(20, 10, 50, color('red'));
  quadrille.rand(50, color('green')).rand(50, color('blue')).
            rand(50, color('cyan'));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.cellLength = 20;
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
  if (quadrille.height < 20) {
    quadrille.insert(quadrille.mouseRow);
  }
}

function keyPressed() {
  reset();
}

function reset() {
  quadrille = createQuadrille(20, 10, 50, color('red'));
  quadrille.rand(50, color('green')).rand(50, color('blue')).
            rand(50, color('cyan'));
}
```
{{< /details >}}

# Syntax

> `insert(row)`

# Parameters

| parameter | description                                                                     |
|-----------|---------------------------------------------------------------------------------|
| row       | Number: number of the row to be inserted [\[0..height\]]({{< ref "height" >}})] |