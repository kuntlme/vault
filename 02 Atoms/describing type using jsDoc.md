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
`shape.js`
```ts  
/**
 * calculate income tax
 * @param {number} income 
 * @returns {number}
 */
export function calculateTax(income){
  return income * 2;
}
```
`index.ts`
```ts
import { calculateTax } from "./shapes";

console.log(calculateTax(34));
```