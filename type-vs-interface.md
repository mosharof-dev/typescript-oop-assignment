# Type vs Interface in TypeScript

## Introduction

TypeScript provides two main ways to define custom types: `type` aliases and `interface`. Both help developers describe the structure of data and make code safer. At first glance, they look very similar because both can define object types. However, they have some key differences in how they work.

## What is Type Alias?

A `type` alias creates a custom name for any type. It supports primitive types, objects, unions, intersections, and tuples.

```ts
type User = {
  name: string;
  age: number;
};

type Status = "active" | "inactive";
```

Here, `User` defines an object structure, and `Status` defines a union of two string values.

## What is Interface?

An `interface` mainly describes the shape of an object. It is commonly used to define object structures and class contracts.

```ts
interface User {
  name: string;
  age: number;
}
```

We can easily extend an interface using the `extends` keyword:

```ts
interface Admin extends User {
  role: string;
}
```

## Core Differences

- `type` supports union (`|`), intersection (`&`), and primitive types, while `interface` only works with objects.
- `interface` supports declaration merging, but `type` does not.
- `interface` uses `extends` for inheritance, while `type` uses intersection (`&`).

For example, two interfaces with the same name automatically merge their properties into one. On the other hand, type aliases cannot be declared multiple times with the same name.

## When Should We Use Them?

Use `interface` when defining object structures, API models, or class contracts. Use `type` when working with unions, intersections, primitives, or complex type combinations.

## Conclusion

Both `type` and `interface` are very useful tools in TypeScript. The right choice depends on your project needs and team style. Understanding both helps developers write clean, safe, and maintainable code.
