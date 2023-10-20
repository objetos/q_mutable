---
weight: 7
draft: false
---

# `randomize()`

Randomly re-arranges the quadrille cells.

# Example

(mouse click to randomize; press any key to reset)\
{{< p5-global-iframe lib1="/p5.quadrille.js/docs/libs/p5.quadrille.js" width="537" height="537" >}}
`use strict`;
Quadrille.CELL_LENGTH = 32;
let mandrill;
let quadrille;

function preload() {
  mandrill = loadImage('../mandrill.png');
}

function setup() {
  createCanvas(512, 512);
  quadrille = createQuadrille(16, mandrill);
}

function draw() {
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.randomize();
}

function keyPressed() {
  quadrille = createQuadrille(16, mandrill);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 32;
let mandrill;
let quadrille;

function preload() {
  mandrill = loadImage('mandrill.png');
}

function setup() {
  createCanvas(512, 512);
  quadrille = createQuadrille(16, mandrill);
}

function draw() {
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.randomize();
}

function keyPressed() {
  quadrille = createQuadrille(16, mandrill);
}
```
{{< /details >}}

# Syntax

> `randomize()`