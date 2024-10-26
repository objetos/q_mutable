---
weight: 4 
title: fill(row, value)  
---

Fills an entire row in the quadrille with the specified `value`.

## Example

(click on a row to fill it with white; press any key to reset)  
{{< p5-global-iframe quadrille="true" width="425" height="425" >}}  
`use strict`;  
Quadrille.cellLength = 20;  
let quadrille;  

function setup() {  
  createCanvas(400, 400);  
  reset();  
}  

function draw() {  
  background('black');  
  drawQuadrille(quadrille);  
}  

function mouseClicked() {  
  const row = quadrille.mouseRow;  
  quadrille.fill(row, 255);  
}  

function keyPressed() {
  reset();  
}  

function reset() {  
  quadrille = createQuadrille(20, 20, 100, color('red'));  
  quadrille.rand(100, color('lime')).rand(100, color('blue'));  
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
  background('black');  
  drawQuadrille(quadrille);  
}  

function mouseClicked() {  
  const row = quadrille.mouseRow;  
  quadrille.fill(row, 255);  
}  

function keyPressed() {  
  reset();  
}  

function reset() {  
  quadrille = createQuadrille(20, 20, 100, color('red'));  
  quadrille.rand(100, color('lime')).rand(100, color('blue'));  
}  
```  
{{< /details >}}  

## Syntax  

> `fill(row, value)`  

## Parameters  

| parameter | description                                                                     |  
|-----------|---------------------------------------------------------------------------------|  
| row       | Number: The row index to fill [\[0..height\]]({{< ref "height" >}})             |  
| value     | Any: The value to fill each cell in the row. Can be color, image, string, etc.  |