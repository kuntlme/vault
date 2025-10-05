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
type Draggable = {
  drag: () => void;
};
type Resizable = {
  resize: () => void;
};
type UIwidget = Draggable & Resizable;

let textbox: UIwidget = {
  drag: () => {},
  resize: () => {},
};
```
