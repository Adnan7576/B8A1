# Type Narrowing in TypeScript: A Practical Guide

In TypeScript, union types allow variables to hold multiple distinct types. Attempting to access members specific to only one type triggers compile-time errors. Type narrowing is the mechanism where TypeScript refines a broad type into a specific type within conditional branches. This guarantees type safety without sacrificing dynamic flexibility. It helps developers eliminate runtime errors before code executes in production.

The compiler analyzes control flow to determine the most accurate type. The `typeof` type guard inspects primitive values at runtime, supporting primitives like `string`, `number`, and `boolean`.

```ts
function formatValue(input: string | number): string {
  if (typeof input === "number") {
    return input.toFixed(2);
  }
  return input.trim();
}
```

Inside the `if` branch, TypeScript narrows `input` to `number`. In the fallback branch, the compiler recognizes `input` as a `string`.

To differentiate class instances, TypeScript utilizes the `instanceof` type guard. This operator checks the prototype chain of an object.

```ts
function logError(error: unknown): string {
  if (error instanceof Error) {
    return error.message;
  }
  return String(error);
}
```

Here, `error.message` is safely accessed only after verifying the instance.

Lastly, the `in` operator narrows object types by checking for specific property keys. It determines property presence across different object shapes.

```ts
type Admin = { permissions: string[] };
type Guest = { role: string };

function authorize(user: Admin | Guest): boolean {
  if ("permissions" in user) {
    return user.permissions.includes("admin");
  }
  return false;
}
```

The compiler verifies `permissions` exists on `user`, safely treating it as `Admin`.

In conclusion, type narrowing allows developers to write robust JavaScript with strict static guarantees. Leveraging `typeof`, `instanceof`, and `in` eliminates unsafe type assertions.
