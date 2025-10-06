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
this help to define own type in creation of object.
T for template.
```ts
class KeyValuePair<T> {
  constructor(
    public key: T,
    public value: string,
  ) {}
}

let pair1 = new KeyValuePair<string>("1", "a");
let pair2 = new KeyValuePair<number>(2, "b");
```

if we do not define the generic in object creation time.
compiler automatically understand the type.
```ts
class KeyValuePair<K, V> {
  constructor(
    public key: K,
    public value: V,
  ) {}
}

let pair1 = new KeyValuePair<string, string>("1", "a");
let pair2 = new KeyValuePair(2, "b");
```