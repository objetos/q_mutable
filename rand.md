---
weight: 6
draft: false
---

# `rand()`

Randomly fills quadrille cells with `pattern` the specified number of `times`.

# Examples

The `rand()` method is exemplified in [reflect]({{< ref "reflect#example" >}}), [rotate]({{< ref "rotate#example" >}}), [transpose]({{< ref "transpose#example" >}}), [magnitude]({{< ref "magnitude#example" >}}), [ring]({{< ref "ring#example" >}}), [clear]({{< ref "clear#example" >}}), [fill]({{< ref "fill#example" >}}), [delete]({{< ref "delete#example" >}}), [insert]({{< ref "insert#example" >}}), [replace]({{< ref "replace#example" >}}), [visit_quadrille]({{< ref "visit_quadrille#examples" >}}), [width]({{< ref "width#example" >}}), [height]({{< ref "height#example" >}}) and [size]({{< ref "size#example" >}}).

# Syntax

> `rand(times, pattern = null)`

# Parameters

| parameter | description                                                                                                                                                         |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| times     | Number: number of repetitions cells                                                                                                                            |
| pattern   | [p5.Image](https://p5js.org/reference/#/p5.Image) \| [p5.Graphics](https://p5js.org/reference/#/p5.Graphics) \| [p5.Color](https://p5js.org/reference/#/p5.Color) \| array \| object \| string \| number \| `null`: empty cells |