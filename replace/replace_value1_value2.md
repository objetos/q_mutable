---
weight: 2
title: replace(value1, value2)  
---

Replaces all cells containing `value1` — matched by identity (`===`) — with `value2`. The two-arg sibling of [replace(value)]({{< ref "replace_value" >}}), which retargets every filled cell instead.

## Example

(click on any cell to replace all cells with the same value with a 🙈; press any key to reset)\
{{< p5 quadrille="true" >}}  
'use strict';  
Quadrille.cellLength = 40;
let quadrille;  
let tomato, lime, dodgerblue;

function setup() {  
  createCanvas(400, 400);  
  tomato = color('tomato');  
  lime = color('lime');  
  dodgerblue = color('dodgerblue');  
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
  quadrille = createQuadrille(10, 10, 25, tomato);
  quadrille.rand(25, lime).rand(25, dodgerblue);  
}
{{< /p5 >}}  

{{% details title="code" open=true %}}  
```js  
Quadrille.cellLength = 40;
let quadrille;  
let tomato, lime, dodgerblue;

function setup() {  
  createCanvas(400, 400);  
  tomato = color('tomato');  
  lime = color('lime');  
  dodgerblue = color('dodgerblue');  
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
  quadrille = createQuadrille(10, 10, 25, tomato);
  quadrille.rand(25, lime).rand(25, dodgerblue);  
}
```  
{{% /details %}}  

<!--the shared-instance identity thread now spans fill_value / replace / clear-flood / search (2026-08-01); Foundations Data (REORG Stage 6) states empty-is-null and value identity day one-->

{{< callout type="info" >}}   
`value1` is matched by **identity** (`===`), so all cells meant to be caught must share the **same instance** — the classic gotcha with object values like colors; see the identity note in [fill(value)]({{< ref "fill_value" >}}) and strict [search]({{< ref "search" >}}). The example dodges it by storing each color once and reusing the variable.
{{< /callout >}}

## Syntax  

> `replace(value1, value2)`  

## Parameters  

| Param     | Description                   |  
|-----------|-------------------------------|  
| `value1`  | Any: A valid JavaScript value |  
| `value2`[^1] | Any: A valid JavaScript value |  

[^1]: A plain function `value2` is **stored, not called** — it becomes a per-cell display routine `({ row, col, options }) => { ... }` (see [`options`]({{< relref display_fns >}})). To have a function **evaluated per cell** at replace time — a fresh object or a varied tile per cell — tag it: `Quadrille.factory(({ row, col }) => new Object(...))`.