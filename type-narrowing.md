# Type Narrowing in TypeScript

## Introduction

TypeScript allows us to use multiple types for a single variable with union types. But sometimes we need to perform an operation that only works with a specific type. This is where type narrowing becomes useful.

Type narrowing helps TypeScript understand the exact type of a value by checking certain conditions. It makes our code safer and helps prevent unexpected errors.

## How Type Narrowing Works

There are several ways to narrow types in TypeScript.

### 1. Using typeof

The `typeof` operator is commonly used to check basic types like string and number.

```typescript
function showResult(value: string | number) {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value * 2;
}
```

Here, TypeScript knows that `value` is a string inside the `if` block and a number outside it.

### 2. Using instanceof

We can use `instanceof` to check whether an object belongs to a particular class.

```typescript
function checkDate(value: Date | string) {
  if (value instanceof Date) {
    return value.getFullYear();
  }
  return value;
}
```

### 3. Using the in Operator

The `in` operator checks whether a property exists in an object.

```typescript
type Car = { drive: () => void };
type Bike = { ride: () => void };

function start(vehicle: Car | Bike) {
  if ("drive" in vehicle) {
    vehicle.drive();
  } else {
    vehicle.ride();
  }
}
```

## Conclusion

Type narrowing is an important feature of TypeScript. It allows us to work with different types confidently. By using `typeof`, `instanceof`, and `in`, we can write code that is easier to understand, maintain, and debug.