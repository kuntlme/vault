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
// interface is like abstract class
abstract class Calender {
  constructor(public name: string) {}

  abstract addEvent(): void;
  abstract removeEvent(): void;
}

interface ICalender {
  name: string;
  addEvent(): void;
  removeEvent(): void;
}
```

```ts
// interface is like abstract class

// abstract class Calender {
//  constructor(public name: string) {}

//  abstract addEvent(): void;
//  abstract removeEvent(): void;
// }

interface Calender {
  name: string;
  addEvent(): void;
  removeEvent(): void;
}

interface CloudCalender extends Calender {
  sync(): void;
}

class GoogleCalender implements Calender {
  constructor(public name: string) {
    this.name = name;
  }

  addEvent(): void {
    throw new Error("Method not implemented.");
  }
  removeEvent(): void {
    throw new Error("Method not implemented.");
  }
}
```