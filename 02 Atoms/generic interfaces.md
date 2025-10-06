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
interface Result<T> {
  data: T | null;
  error: string | null;
}
function fetch<T>(url: string): Result<T> {
  return { data: null, error: null };
}

interface User {
  username: string;
}

interface Product {
  title: string;
}

let productResult = fetch<Product>("url");
productResult.data?.title;

let userResult = fetch<User>("url");
userResult.data?.username;
```