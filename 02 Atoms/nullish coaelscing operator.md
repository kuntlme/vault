---
aliases:
tags:
  - atom
  - coding
Reference Link: (insert link to book)
Page Number:
Topics:
  - TypeScript
---
in js use use speed || 30 but it return 30 when speed is falsy 
falsy means -> null | undefined | ' ' | 0 ;
but 0 is a valid but it think it like falsy and it return 30
but when we use `??` it only understand nulllish means undefined | null
``` ts
let speed: number | null = 0;
let ride = {
  speed: speed ?? 30,
};
console.log(ride.speed);
```