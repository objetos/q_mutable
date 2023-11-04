---
bookCollapseSection: true
weight: 4
draft: false
---

# Mutators

Mutator methods directly modify the state of the `quadrille` they are called upon. These transformations are persistent and affect the `quadrille` instance in-place.

{{< hint info >}}
**Observation**\
Methods in this category support [method chaining](https://en.wikipedia.org/wiki/Method_chaining), allowing multiple modifications to be applied sequentially in a concise manner. For example, `quadrille.clear().fill(5, '🐁').randomize()` is functionally equivalent to applying each method separately:
```js
quadrille.clear();
quadrille.fill(5, '🐁');
quadrille.randomize();
```
{{< /hint >}}