---
weight: 4
draft: false
title: randomize()
---

Randomly re-arranges the quadrille cells.

## Example

(mouse click to randomize; press any key to reset)\
{{< p5 quadrille="true" >}}
'use strict';
Quadrille.cellLength = 32;
let mandrill;
let quadrille;

async function setup() {
  createCanvas(512, 512);
  mandrill = await loadImage('/images/mandrill.png');
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
{{< /p5 >}}

{{% details title="code" open=true %}}
```js
Quadrille.cellLength = 32;
let mandrill;
let quadrille;

async function setup() {
  createCanvas(512, 512);
  mandrill = await loadImage('/images/mandrill.png');
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
{{% /details %}}

{{< callout type="info" >}}
For deterministic (repeatable) randomness, explicitly call [randomSeed(seed)](https://p5js.org/reference/p5/randomSeed/) before `randomize()`.
{{< /callout >}}

## Syntax

> `randomize()`
