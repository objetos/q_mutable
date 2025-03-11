---
weight: 6
title: fill(row, col, value, directions, border)  
---

Fills a specific cell and all connected cells in the quadrille with the specified `value`, based on the given `directions` and `border` options, using a [flood fill](https://en.wikipedia.org/wiki/Flood_fill) algorithm.

## Example

(click on any cell to perform flood fill based on selected options; press any key to reset)  
{{< p5-global-iframe quadrille="true" width="425" height="445" >}}  
'use strict';  
Quadrille.cellLength = 20;  
let quadrille;  
let mode;  

function setup() {  
  createCanvas(400, 400);  
  mode = createSelect();  
  mode.option('flood fill 4-directions');  
  mode.option('flood fill 4-directions border');  
  mode.option('flood fill 8-directions');  
  mode.option('flood fill 8-directions border');  
  mode.selected('flood fill 4-directions');  
  reset();  
}  

function draw() {  
  background('black');  
  drawQuadrille(quadrille);  
}  

function mouseClicked() {  
  const row = quadrille.mouseRow;  
  const col = quadrille.mouseCol;  
  switch (mode.value()) {  
    case 'flood fill 4-directions':  
      quadrille.fill(row, col, 255, 4);  
      break;  
    case 'flood fill 4-directions border':  
      quadrille.fill(row, col, 255, 4, true);  
      break;  
    case 'flood fill 8-directions':  
      quadrille.fill(row, col, 255, 8);  
      break;  
    case 'flood fill 8-directions border':  
      quadrille.fill(row, col, 255, 8, true);  
      break;  
  }  
}  

function keyPressed() {  
  reset();  
}  

function reset() {  
  quadrille = createQuadrille(20, 20, 100, color('red'));  
  quadrille.rand(100, color('lime')).rand(100, color('blue'));
}  
{{< /p5-global-iframe >}}  

{{% details title="code" open=true %}}  
```js  
Quadrille.cellLength = 20;  
let quadrille;  
let mode;  

function setup() {  
  createCanvas(400, 400);  
  mode = createSelect();  
  mode.option('flood fill 4-directions');  
  mode.option('flood fill 4-directions border');  
  mode.option('flood fill 8-directions');  
  mode.option('flood fill 8-directions border');  
  mode.selected('flood fill 4-directions');  
  reset();  
}  

function draw() {  
  background('black');  
  drawQuadrille(quadrille);  
}  

function mouseClicked() {  
  const row = quadrille.mouseRow;  
  const col = quadrille.mouseCol;  
  switch (mode.value()) {  
    case 'flood fill 4-directions':  
      quadrille.fill(row, col, 255, 4);  
      break;  
    case 'flood fill 4-directions border':  
      quadrille.fill(row, col, 255, 4, true);  
      break;  
    case 'flood fill 8-directions':  
      quadrille.fill(row, col, 255, 8);  
      break;  
    case 'flood fill 8-directions border':  
      quadrille.fill(row, col, 255, 8, true);  
      break;  
  }  
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

> `fill(row, col, value, directions, border)`  

## Parameters  

| Param        | Description                                                                                          |  
|--------------|------------------------------------------------------------------------------------------------------|  
| `row`        | Number: row index of the cell to start filling [[0..height]]({{< ref "height" >}})                 |  
| `col`        | Number: column index of the cell to start filling [[0..width]]({{< ref "width" >}})                |  
| `value`      | Any: A valid JavaScript value                                                                        | 
| `directions` | Number: Number of directions for flood fill (4 or 8), default is 4                                   |  
| `border`     | Boolean: Specifies whether to include the border of the flood fill area. Default is `false`          | 