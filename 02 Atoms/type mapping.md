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
```ts
interface Product {
  name: string;
  price: number;
}

type ReadonlyProduct = {
  // index signature
  // keyof

  readonly [Property in keyof Product]: Product[Property];
  // we can write anything in place of Property
  // in generic term we use K where K for keyof
};

// generic readonly type
type ReadOnly<T> = {
  readonly [K in keyof T]: T[K];
};

type Optional<T> = {
  readonly [K in keyof T]?: T[K];
};

type Nullable<T> = {
  readonly [K in keyof T]: T[K] | null;
};
```
