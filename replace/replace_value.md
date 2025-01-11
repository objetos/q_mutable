---
weight: 1
title: replace(value)
---

Replaces all non-empty cells in the quadrille with the specified `value`.

## Example

(click or press any key to toggle between replacing cells and resetting)\
{{< p5-global-iframe quadrille="true" width="425" height="425" >}}  
'use strict';  
Quadrille.cellLength = 40;
let quadrille;
let replaced = false;

function setup() {  
  createCanvas(400, 400);
  reset();  
}  

function draw() {  
  background('black');  
  drawQuadrille(quadrille);  
}  

function mouseClicked() {
  replaced = !replaced;
  replaced ? quadrille.replace('🐛') : reset();
}  

function keyPressed() {  
  replaced = !replaced;
  replaced ? quadrille.replace('🙈') : reset();
}  

function reset() {  
  quadrille = createQuadrille(10, 10, 25, color('red'));
  quadrille.rand(25, color('lime')).rand(25, color('blue'));  
}  
{{< /p5-global-iframe >}}  

{{< details title="code" open=false >}}  
```js  
Quadrille.cellLength = 40;
let quadrille;
let replaced = false;

function setup() {  
  createCanvas(400, 400);
  reset();  
}  

function draw() {  
  background('black');  
  drawQuadrille(quadrille);  
}  

function mouseClicked() {
  replaced = !replaced;
  replaced ? quadrille.replace('🐛') : reset();
}  

function keyPressed() {  
  replaced = !replaced;
  replaced ? quadrille.replace('🙈') : reset();
}  

function reset() {  
  quadrille = createQuadrille(10, 10, 25, color('red'));
  quadrille.rand(25, color('lime')).rand(25, color('blue'));  
}  
```  
{{< /details >}}  

## Syntax  

> `replace(value)`  

## Parameters  

| Param     | Description                                                                                                                                                        |  
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| `value`   | Any: A valid JavaScript value                                                        |