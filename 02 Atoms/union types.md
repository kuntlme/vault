---
aliases:
tags:
  - atom
  - coding
Reference Link: (insert link to book)
Page Number:
Topics:
---

``` ts
function calc(weight: number | string): number {
  if (typeof weight === "number") {
    return weight * 202;
  } else {
    return parseInt(weight) * 202;
  }
}

console.log(calc(23));
```