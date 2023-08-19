---
weight: 8
draft: false
---

# `sort()`

Sort quadrille cells according to their coloring.

# Syntax

> `sort([{[mode], [target], [ascending], [textColor], [textZoom], [outline], [background], [numberColor], [min], [max]}])`

# Parameters

| parameter   | description                                                                                              |
|-------------|----------------------------------------------------------------------------------------------------------|
| mode        | String: Either `LUMA`, `AVG`, or `DISTANCE` default is `LUMA`.                                           |
| target      | [p5.Color](https://p5js.org/reference/#/p5.Color) representation: `DISTANCE` mode target color           |
| ascending   | Boolean: sort cells ascending default is true.                                                           |
| textColor   | [p5.Color](https://p5js.org/reference/#/p5.Color) representation: text sampling color default is `black` |
| textZoom    | Number:: text zoom level default is `0.89`                                                               |
| background  | [p5.Color](https://p5js.org/reference/#/p5.Color) representation: background sampling default is `white` |
| cellLength  | Number: cell sampling length default is quadrille [width](/docs/props#width)                             |
| numberColor | [p5.Color](https://p5js.org/reference/#/p5.Color) representation: number color default is `orange`       |
| min         | Number: remap cell alpha when its entry is a number from [min, max] to [0, 255] number default is `0`    |
| max         | Number: remap cell alpha when its entry is a number from [min, max] to [0, 255] number default is `0`    |