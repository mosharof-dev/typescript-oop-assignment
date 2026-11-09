# Type Narrowing in TypeScript

## Introduction

Type Narrowing is an important feature of TypeScript. It helps developers check a variable's type before using it. When a variable has a union type, it can hold more than one type of value. Because of this, we cannot directly use methods that belong to only one specific type. Type narrowing solves this problem and helps prevent runtime errors.

TypeScript supports different ways to narrow types, such as `typeof`, `instanceof`, and the `in` operator.

## 1. typeof Operator

The `typeof` operator checks the basic type of a value, like string, number, or boolean. It is very useful when working with simple union types.

```ts
function processValue(value: string | number): void {
  if (typeof value === "string") {
    console.log(value.toUpperCase());
  } else {
    console.log(value * 2);
  }
}
```

Here, TypeScript knows that the value is a string inside the `if` block and a number inside the `else` block. This allows us to call `toUpperCase()` safely without any error.

## 2. instanceof Operator

The `instanceof` operator checks whether an object is created from a specific class. We use it when working with classes and custom objects.

```ts
class Car {
  drive(): void {
    console.log("Car is driving");
  }
}

function start(vehicle: Car | Date): void {
  if (vehicle instanceof Car) {
    vehicle.drive();
  }
}
```

Here, TypeScript knows that `vehicle` is a `Car` inside the condition, so calling `drive()` is completely safe.

## 3. in Operator

The `in` operator checks whether an object has a specific property name. It helps us separate different object types that do not share the same properties.

```ts
type Admin = { role: string };
type User = { email: string };

function showInfo(person: Admin | User): void {
  if ("role" in person) {
    console.log(person.role);
  } else {
    console.log(person.email);
  }
}
```

In this example, TypeScript checks if `role` exists inside `person`. If it exists, TypeScript treats `person` as an `Admin`, otherwise as a `User`.

## Conclusion

Type Narrowing helps TypeScript understand the exact type of a value at different points in the code. Using `typeof`, `instanceof`, and `in` makes our code safer, clearer, and much easier to maintain.
