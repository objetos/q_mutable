---
weight: 7
title: fill(row, col, value)  
---

Fills a specific cell in the quadrille with the specified `value`.

## Example

(click on any cell to fill it with white; press any key to reset)  
{{< p5 quadrille="true" >}}  
'use strict';  
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
  const col = quadrille.mouseCol;  
  quadrille.fill(row, col, 255);  
}  

function keyPressed() {  
  reset();  
}  

function reset() {  
  quadrille = createQuadrille(20, 20, 100, color('red'));  
  quadrille.rand(100, color('lime')).rand(100, color('blue'));
}  
{{< /p5 >}}  

{{% details title="code" open=true %}}  
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
  const col = quadrille.mouseCol;  
  quadrille.fill(row, col, 255);  
}  

function keyPressed() {  
  reset();  
}  

function reset() {  
  quadrille = createQuadrille(20, 20, 100, color('red'));  
  quadrille.rand(100, color('lime')).rand(100, color('blue'));
}  
```  
{{% /details %}}  

## Syntax  

> `fill(row, col, value)`  

## Parameters  

| Param     | Description                                                                          |  
|-----------|--------------------------------------------------------------------------------------|  
| `row`     | Number: row number of the cell to fill [[0..height]]({{< ref "height" >}})         |  
| `col`     | Number: column number of the cell to fill [[0..width]]({{< ref "width" >}})        |  
| `value`[^1] | Any: A valid JavaScript value                                                        |  

[^1]: A plain function `value` is **stored, not called** — it becomes a per-cell display routine `({ row, col, options }) => { ... }` (see [`options`]({{< relref display_fns >}})). To have a function **evaluated per cell** at fill time — a fresh object or a varied tile per cell — tag it: `Quadrille.factory(({ row, col }) => new Object(...))`.