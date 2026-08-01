---
weight: 5
draft: false
title: "maze(value)"
---

Clears the quadrille, then generates a [perfect maze](https://en.wikipedia.org/wiki/Maze_generation_algorithm) at the current dimensions, filling wall cells with `value` — the maze analogue of the zero-arg [fill()]({{< ref "fill_noargs" >}}) chessboard. The generator is an iterative [randomized depth-first search](https://en.wikipedia.org/wiki/Maze_generation_algorithm#Iterative_implementation_%28with_explicit_stack%29) over the room lattice. Walls are filled cells and corridors are empty cells, so [reach]({{< ref "reach" >}}) and [path]({{< ref "path" >}}) work on the result out of the box. Rooms sit at even `(row, col)` indices, cell `(0, 0)` is always open, and the maze is borderless: the quadrille edge bounds it. Perfect means any two empty cells are joined by exactly one path, so no start or end cells are needed. Returns the quadrille (**chainable**).

## Example

(click to regenerate; press any key to toggle fat ⇄ thin)\
{{< p5 quadrille="true" >}}
'use strict';
Quadrille.cellLength = 30;
let board;
let wall;
let thin = false;
const THIN = {
  colorDisplay: Quadrille.thinWall, imageDisplay: Quadrille.thinWall,
  stringDisplay: Quadrille.thinWall, numberDisplay: Quadrille.thinWall,
  tileDisplay: null, outlineWeight: 7
};

function setup() {
  createCanvas(11 * Quadrille.cellLength, 15 * Quadrille.cellLength);
  wall = color('#0b332b');
  board = createQuadrille(11, 15).maze(wall);
}

function draw() {
  background('#138a72');
  drawQuadrille(board, thin ? { ...THIN, outline: '#0b332b' } : { outlineWeight: 0.5 });
}

function mousePressed() {
  board.maze(wall); // fresh level, one call
}

function keyPressed() {
  key.length === 1 && (thin = !thin); // fat ⇄ thin: a param swap
}
{{< /p5 >}}

{{% details title="code" open=true %}}
```js
Quadrille.cellLength = 30;
let board;
let wall;
let thin = false;
const THIN = {
  colorDisplay: Quadrille.thinWall, imageDisplay: Quadrille.thinWall,
  stringDisplay: Quadrille.thinWall, numberDisplay: Quadrille.thinWall,
  tileDisplay: null, outlineWeight: 7
};

function setup() {
  createCanvas(11 * Quadrille.cellLength, 15 * Quadrille.cellLength);
  wall = color('#0b332b');
  board = createQuadrille(11, 15).maze(wall);
}

function draw() {
  background('#138a72');
  drawQuadrille(board, thin ? { ...THIN, outline: '#0b332b' } : { outlineWeight: 0.5 });
}

function mousePressed() {
  board.maze(wall); // fresh level, one call
}

function keyPressed() {
  key.length === 1 && (thin = !thin); // fat ⇄ thin: a param swap
}
```
{{% /details %}}

{{< callout type="info" >}}
Regeneration, restyling, and the fat ⇄ thin toggle never touch storage: walls stay whatever they are, and the thin look is a display swap at the draw site via [Quadrille.thinWall]({{< relref "thin_wall" >}}) — installed as every display with `tileDisplay: null`, styled by the draw call's own [outline]({{< relref "outline" >}}) and [outlineWeight]({{< relref "outline_weight" >}}).
{{< /callout >}}

{{< callout type="warning" >}}
Odd dimensions are canonical. On even ones a warning is issued and the trailing even row/col — which holds no rooms — seals as a wall strip on that side.
{{< /callout >}}

{{< callout type="info" >}}
`value` goes through [fill]({{< ref "fill" >}}) internals, so the `Quadrille.factory` contract is honored: a plain function is stored as a display-contract wall drawing, whereas a factory-tagged one is evaluated per wall cell — e.g. `board.maze(Quadrille.factory(() => random(['🧱', '🪨'])))` yields varied wall tiles.
{{< /callout >}}

{{< callout type="info" >}}
**Recipes**
- **Braiding:** `board.maze(wall).rand(k)` clears `k` random filled cells, turning a perfect maze into a loopy one.
- **Level authoring:** `createQuadrille(w, h).maze(wall)` → [toBigInt]({{< ref "to_bigint" >}}) → ship the result as a `const` bitboard. Decode with the **same dimensions and endianness**: a mismatched decode shifts the pattern.
- **Pathfinding:** [reach]({{< ref "reach" >}}) and [path]({{< ref "path" >}}) treat any filled cell as an obstacle — no maze required.
{{< /callout >}}

{{< callout type="info" >}}
For deterministic (repeatable) mazes, explicitly call [randomSeed(seed)](https://p5js.org/reference/p5/randomSeed/) before `maze(value)`.
{{< /callout >}}

## Syntax

> `maze(value)`

## Parameters

| Param   | Description                                                                                                                                     |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `value` | Any: wall value — a literal (color, string, image, …), a display-contract function (stored as-is), or a `Quadrille.factory`-tagged function (evaluated per wall cell) |
