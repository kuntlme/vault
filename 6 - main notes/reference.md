Here’s a starter set of “primitive” components to drop into your Puck palette. You can register each with `createComponent` so authors can compose pages from these building blocks:

---

### 1. `<Heading>`

Wraps any of the six HTML headings.

```tsx
import { createComponent } from "@puckjs/core";

export const Heading = createComponent({
  name: "Heading",
  props: {
    level: {
      type: "enum",
      options: ["h1","h2","h3","h4","h5","h6"],
      defaultValue: "h1",
    },
    text: {
      type: "string",
      defaultValue: "Your Heading Here",
    },
    align: {
      type: "enum",
      options: ["left","center","right"],
      defaultValue: "left",
    },
    color: {
      type: "string",
      defaultValue: "#000000",
    },
    fontSize: {
      type: "number",
      defaultValue: 32,
    },
  },
  render: ({ level, text, align, color, fontSize }) => {
    const Tag = level as keyof JSX.IntrinsicElements;
    return (
      <Tag style={{ textAlign: align, color, fontSize: `${fontSize}px` }}>
        {text}
      </Tag>
    );
  },
});
```

---

### 2. `<TextBlock>`

A generic paragraph/text component.

```tsx
export const TextBlock = createComponent({
  name: "TextBlock",
  props: {
    text: { type: "string", defaultValue: "Insert your text here…" },
    fontSize: { type: "number", defaultValue: 16 },
    lineHeight: { type: "number", defaultValue: 1.5 },
    color: { type: "string", defaultValue: "#333333" },
    align: {
      type: "enum",
      options: ["left","center","right","justify"],
      defaultValue: "left",
    },
  },
  render: ({ text, fontSize, lineHeight, color, align }) => (
    <p style={{ fontSize: `${fontSize}px`, lineHeight, color, textAlign: align }}>
      {text}
    </p>
  ),
});
```

---

### 3. `<Card>`

A simple container with optional title, image, and content slot.

```tsx
export const Card = createComponent({
  name: "Card",
  props: {
    title: { type: "string", defaultValue: "Card Title" },
    imageUrl: { type: "string", defaultValue: "" },
    imageHeight: { type: "number", defaultValue: 150 },
    borderRadius: { type: "number", defaultValue: 8 },
    boxShadow: { type: "string", defaultValue: "0 2px 8px rgba(0,0,0,0.1)" },
    content: { type: "slot" },
  },
  render: ({ title, imageUrl, imageHeight, borderRadius, boxShadow, content }) => (
    <div style={{ borderRadius, boxShadow, overflow: "hidden" }}>
      {imageUrl && (
        <img src={imageUrl} style={{ width: "100%", height: imageHeight }} alt={title} />
      )}
      <div style={{ padding: 16 }}>
        <h3 style={{ margin: "0 0 8px" }}>{title}</h3>
        <div>{content}</div>
      </div>
    </div>
  ),
});
```

---

### 4. `<Button>`

Configurable button with text, variant, and click slot.

```tsx
export const Button = createComponent({
  name: "Button",
  props: {
    text: { type: "string", defaultValue: "Click me" },
    variant: {
      type: "enum",
      options: ["solid","outline","text"],
      defaultValue: "solid",
    },
    color: { type: "string", defaultValue: "#007bff" },
    size: {
      type: "enum",
      options: ["small","medium","large"],
      defaultValue: "medium",
    },
    onClick: { type: "event" },
  },
  render: ({ text, variant, color, size, onClick }) => {
    const padding = size === "large" ? "12px 24px" : size === "small" ? "4px 12px" : "8px 16px";
    const styles = {
      padding,
      border: variant === "outline" ? `2px solid ${color}` : "none",
      background: variant === "solid" ? color : "transparent",
      color: variant === "solid" ? "#fff" : color,
      cursor: "pointer",
      borderRadius: 4,
    };
    return (
      <button style={styles} onClick={onClick}>
        {text}
      </button>
    );
  },
});
```

---

### 5. `<ImageBlock>`

For standalone images.

```tsx
export const ImageBlock = createComponent({
  name: "ImageBlock",
  props: {
    src: { type: "string", defaultValue: "" },
    alt: { type: "string", defaultValue: "Image description" },
    width: { type: "number", defaultValue: 300 },
    height: { type: "number", defaultValue: 200 },
    fit: {
      type: "enum",
      options: ["cover","contain","fill","none"],
      defaultValue: "cover",
    },
  },
  render: ({ src, alt, width, height, fit }) => (
    <img src={src} alt={alt} style={{ width, height, objectFit: fit }} />
  ),
});
```

---

#### How to wire them into Puck

In your Puck setup file:

```ts
import { registerComponent } from "@puckjs/core";
import { Heading, TextBlock, Card, Button, ImageBlock } from "./primitives";

[Heading, TextBlock, Card, Button, ImageBlock].forEach(registerComponent);
```

Now your authors will see **Heading**, **TextBlock**, **Card**, **Button**, and **ImageBlock** in the component toolbar—ready to drag onto their canvas and configure via props.

Feel free to extend these with additional style props (margins, padding, borders) or add new primitives (e.g. `Divider`, `Icon`, `List`).