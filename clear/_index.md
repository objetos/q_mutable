---
bookCollapseSection: true
title: "clear(args)"
weight: 9
---

Clears quadrille cells (i.e., sets cells to `null`): all cells, a predicate-matched set, a given `row`, a bitboard pattern, a given cell, or a connected same-value region via [flood fill](https://en.wikipedia.org/wiki/Flood_fill).

{{< callout type="info" >}}
Use `clear` instead of [fill]({{< relref "fill" >}}) to set cells to `null`.
{{< /callout >}}