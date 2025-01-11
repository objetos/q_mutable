---
weight: 1
title: rand(times, value)
---

Randomly fills the quadrille with the specified `value` a given number of `times`.

## Example

(numeric keys define `times`; other keys define `value`)\
{{< p5-global-iframe quadrille="true" width="385" height="415" >}}  
'use strict';  
Quadrille.cellLength = 30;
let times = 5;
let value, values;
let quadrille;
let p;

function setup() {
  createCanvas(12 * Quadrille.cellLength, 12 * Quadrille.cellLength);
  values = ['👻', '✈️', color('cyan'), 125, '🐒', '🐍'];
  value = '🐒';
  quadrille = createQuadrille(12, 12, 14, value);
  p = createP();
  p.html(`mouse click fills ${times} time(s) with ${value}`);
  p.style('font-size', '16px');
  p.position(10, height);
}

function draw() {
  background('black');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.rand(times, value);
  quadrille.order === quadrille.width * quadrille.height &&
                      (quadrille = createQuadrille(12, 12, 14, value));
}

function keyPressed() {
  +key ? times = +key : value = random(values);
  p.html(`mouse click fills ${times} time(s) with ${value}`);
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
  values = ['👻', '✈️', color('cyan'), 125, '🐒', '🐍'];
  value = '🐒';
  quadrille = createQuadrille(12, 12, 14, value);
  p = createP();
  p.html(`mouse click fills ${times} time(s) with ${value}`);
  p.style('font-size', '16px');
  p.position(10, height);
}

function draw() {
  background('black');
  drawQuadrille(quadrille);
}

function mouseClicked() {
  quadrille.rand(times, value);
  quadrille.order === quadrille.width * quadrille.height &&
                      (quadrille = createQuadrille(12, 12, 14, value));
}

function keyPressed() {
  +key ? times = +key : value = random(values);
  p.html(`mouse click fills ${times} time(s) with ${value}`);
}
```  
{{< /details >}}  

## Syntax  

> `rand(times, value)`  

## Parameters  

| Param     | Description                                                                                                                |  
|-----------|----------------------------------------------------------------------------------------------------------------------------|  
| `times`   | Number: number of cells to fill randomly                                             |  
| `value`   | Any: A valid JavaScript value                                                        |