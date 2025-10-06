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
abstract class Shape {
  constructor(public color: string) {}
  abstract render(): void;
}
class Circle extends Shape {
  constructor(
    public radius: number,
    color: string,
  ) {
    super(color);
  }
  render(): void {
    console.log("circle is rendering");
  }
}
let circle = new Circle(23, "red");
circle.render();
```
