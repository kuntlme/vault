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
create d.ts file with same as js file which file I want to declare.
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
`shapes.d.ts`
```ts
export declare function calculateTax(income:number): number;
```
`index.ts`
```ts
import { calculateTax } from "./shapes";

console.log(calculateTax(34));
```
