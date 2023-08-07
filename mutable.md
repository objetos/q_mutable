---
weight: 5
draft: false
---

# Quadrille mutable methods

The `quadrille` mutable methods are the following:

1. `delete(row)`: deletes the given quadrille `row`.
2. `clear()`, `clear(row)`, `clear(row, col)`: clears quadrille cells. Either all quadrille cells, a given `row` or a cell,  resp.
3. `clear(row, col, directions)`, `clear(row, col, border)`, `clear(row, col, directions, border)`: [flood clear](https://en.m.wikipedia.org/wiki/Flood_fill) using 4 or 8 directions and including (or not) the clearing border.
4. `fill(pattern)`, `fill(row, pattern)`, `fill(row, col, pattern)`: fills quadrille cells with given `pattern` (any data type instance but `undefined` or `null`). Either current empty cells, a whole `row`, or a cell, respectively.
5. `fill(row, col, pattern, directions)`, `fill(row, col, pattern, border)`, `fill(row, col, pattern, directions, border)`: [flood fill](https://en.m.wikipedia.org/wiki/Flood_fill) using 4 or 8 directions and including (or not) the filling area border.
6. `replace(pattern)`, `replace(pattern1, pattern2)`: either replaces non empty cells with `pattern` or searches `pattern1` cell ocurrences and replaces them with `pattern2`, respectively. Both, `pattern1` and `pattern2` are any data type instances but `undefined` or `null`.
7. `insert(row)`: inserts an empty `row` into the quadrille.
8. `rand(order, pattern)`: fills the quadrille with `pattern` (any data type instance but `undefined` or `null`) up to `order` (number of repeations), randomly adding or removing cells as necessary.
9. `randomize()`: randomly re-arranges the quadrille cells.

These methods are pretty straightforward and its usage is left out as an exercise.