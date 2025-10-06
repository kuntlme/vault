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
this help to make dynamic key of a object

```ts
class SeatAssignment {
  [seatNumber: string]: string;
}

let seats = new SeatAssignment();
seats.a1 = "kuntal";
seats.a2 = "kunal";
console.log(seats);
```
