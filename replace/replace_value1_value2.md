---
weight: 2
title: replace(value1, value2)  
---

Replaces all cells containing `value1` with `value2` in the quadrille. 

## Example

(click on any cell to replace all cells with the same value with a 🙈; press any key to reset)\
{{< p5-global-iframe quadrille="true" width="425" height="425" >}}  
`use strict`;  
Quadrille.cellLength = 40;
let quadrille;  
let red, lime, blue, cyan;

function setup() {  
  createCanvas(400, 400);  
  red = color('red');  
  lime = color('lime');  
  blue = color('blue');  
  cyan = color('cyan');  
  reset();  
}  

function draw() {  
  background('black');  
  drawQuadrille(quadrille);  
}  

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  const value = quadrille.read(row, col);
  quadrille.replace(value, '🙈');
}  

function keyPressed() {  
  reset();
}  

function reset() {  
  quadrille = createQuadrille(10, 10, 25, red);
  quadrille.rand(25, lime).rand(25, blue);  
}
{{< /p5-global-iframe >}}  

{{< details title="code" open=false >}}  
```js  
Quadrille.cellLength = 40;
let quadrille;  
let red, lime, blue, cyan;

function setup() {  
  createCanvas(400, 400);  
  red = color('red');  
  lime = color('lime');  
  blue = color('blue');  
  cyan = color('cyan');  
  reset();  
}  

function draw() {  
  background('black');  
  drawQuadrille(quadrille);  
}  

function mouseClicked() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  const value = quadrille.read(row, col);
  quadrille.replace(value, '🙈');
}  

function keyPressed() {  
  reset();
}  

function reset() {  
  quadrille = createQuadrille(10, 10, 25, red);
  quadrille.rand(25, lime).rand(25, blue);  
}
```  
{{< /details >}}  

<!--TODO: move observation below to missed value (data types) pending chapter-->

{{< callout type="info" >}}  
**Observation**  
To replace `value1` with `value2`, all cells containing `value1` must share the same memory reference, see [search()]({{< ref "search" >}}).  
{{< /callout >}}

## Syntax  

> `replace(value1, value2)`  

## Parameters  

| parameter | description                                                                                                                                                        |  
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| value1    | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number |  
| value2    | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number |  