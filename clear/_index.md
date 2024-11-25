---
bookCollapseSection: true
title: "clear(args)"
weight: 7
---

Clears quadrille cells (i.e., sets cells to `null`). Either all cells, a given cell, a given `row` or a set of identical cells using [flood fill](https://en.m.wikipedia.org/wiki/Flood_fill) or all cells.

gpt add callout info: don't set `null` cells directly (e.g., `fill`) but use clear.

{{< callout type="info" >}}
**Observation**\
Use `clear` instead of `fill` to set cells to `null`.
{{< /callout >}}